# REST API

RelishEconomy includes an embedded HTTP API server so external services — Discord bots, web dashboards, automation scripts, and other plugins — can read and modify player balances without touching the database directly.

## Setup

Enable the API in `config.yml`:

```yaml
rest-api:
  enabled: true
  port: 8765
  bind-address: "127.0.0.1"  # use 0.0.0.0 to expose externally
  token: "your-secret-token-here"
```

Restart or `/re reload` after changing these values.

> **Security:** The API binds to `127.0.0.1` by default so it is not reachable from the internet. If you expose it externally, put it behind a reverse proxy (nginx, Caddy) that handles TLS. Always set a strong, random token — leaving it blank denies all requests.

---

## Authentication

Every request must include a Bearer token header:

```
Authorization: Bearer your-secret-token-here
```

Missing or wrong token → `401 Unauthorized`.

---

## Response format

All responses are JSON.

**Success:**
```json
{ "ok": true, "data": { ... } }
```

**Error:**
```json
{ "ok": false, "error": "message" }
```

---

## Endpoints

### `GET /api/v1/status`

Server health snapshot.

```bash
curl -H "Authorization: Bearer <token>" http://localhost:8765/api/v1/status
```

```json
{
  "ok": true,
  "data": {
    "plugin": "RelishEconomy",
    "version": "1.1.7-Beta",
    "online_players": 12,
    "loaded_accounts": 15,
    "currencies": 2,
    "uptime_ms": 86400000
  }
}
```

---

### `GET /api/v1/currencies`

All configured currencies.

```bash
curl -H "Authorization: Bearer <token>" http://localhost:8765/api/v1/currencies
```

```json
{
  "ok": true,
  "data": [
    {
      "name": "dollars",
      "symbol": "$",
      "display_name": "Dollars",
      "default": true,
      "decimals_enabled": true,
      "starting_balance": 100.0,
      "payments_enabled": true
    }
  ]
}
```

---

### `GET /api/v1/player/{uuid}/balance`

All currency balances for a player. Works for online and offline players.

```bash
curl -H "Authorization: Bearer <token>" \
  http://localhost:8765/api/v1/player/069a79f4-44e9-4726-a5be-fca90e38aaf5/balance
```

```json
{
  "ok": true,
  "data": {
    "uuid": "069a79f4-44e9-4726-a5be-fca90e38aaf5",
    "player_name": "Notch",
    "online": false,
    "balances": { "dollars": 1500.00, "coins": 250 }
  }
}
```

---

### `GET /api/v1/player/{uuid}/balance/{currency}`

Single currency balance.

```bash
curl -H "Authorization: Bearer <token>" \
  http://localhost:8765/api/v1/player/{uuid}/balance/dollars
```

```json
{
  "ok": true,
  "data": {
    "uuid": "...",
    "player_name": "Notch",
    "online": false,
    "currency": "dollars",
    "balance": 1500.00
  }
}
```

---

### `POST /api/v1/player/{uuid}/balance/set`

Set a player's balance to an exact amount.

**Body:** `{"currency": "dollars", "amount": 500}`

```bash
curl -X POST \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -d '{"currency":"dollars","amount":500}' \
  http://localhost:8765/api/v1/player/{uuid}/balance/set
```

```json
{
  "ok": true,
  "data": { "uuid": "...", "currency": "dollars", "new_balance": 500 }
}
```

---

### `POST /api/v1/player/{uuid}/balance/add`

Add to a player's balance.

**Body:** `{"currency": "dollars", "amount": 100}`

---

### `POST /api/v1/player/{uuid}/balance/subtract`

Subtract from a player's balance (clamped to 0, never goes negative).

**Body:** `{"currency": "dollars", "amount": 50}`

---

### `POST /api/v1/player/{uuid}/balance/clear`

Zero out one currency or all currencies.

**Body (one currency):** `{"currency": "dollars"}`  
**Body (all currencies):** `{}` or omit the `currency` field

```json
{
  "ok": true,
  "data": { "uuid": "...", "currencies_cleared": 2 }
}
```

---

### `POST /api/v1/player/{uuid}/balance/refresh`

Force-reload the player's account from the database. Use this after your external tool has written directly to the DB so the in-memory cache reflects the change immediately.

**Body:** none required

```json
{
  "ok": true,
  "data": {
    "uuid": "...",
    "player_name": "Notch",
    "online": false,
    "balances": { "dollars": 999.00 }
  }
}
```

---

## Error codes

| HTTP | Meaning |
|------|---------|
| `200` | Success |
| `400` | Bad request — missing or invalid field |
| `401` | Unauthorized — missing or wrong token |
| `404` | Player or currency not found |
| `405` | Method not allowed |
| `500` | Internal server error |

---

## Discord bot example (Python)

```python
import requests

BASE = "http://localhost:8765/api/v1"
HEADERS = {"Authorization": "Bearer your-token"}

# Get a player's balance
r = requests.get(f"{BASE}/player/{uuid}/balance/dollars", headers=HEADERS)
balance = r.json()["data"]["balance"]

# Give 100 dollars as a reward
requests.post(
    f"{BASE}/player/{uuid}/balance/add",
    headers=HEADERS,
    json={"currency": "dollars", "amount": 100}
)
```

---

## Notes

- All write operations (`set`, `add`, `subtract`, `clear`) go through `AccountManager` — cache invalidation, transaction events, and dirty-tracking all fire exactly as they do for in-game commands.
- Requests time out after 8 seconds if the database is unresponsive.
- The server uses a 4-thread pool. Requests are handled off the Bukkit main thread.
- Amount fields accept standard decimal numbers. Negative amounts are rejected.
