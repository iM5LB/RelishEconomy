# Commands Reference

This page documents the commands shipped in `plugin.yml` plus the `/re` subcommands.

## Player Commands (Free)

### Balance

| Command | Description | Permission |
|--------|-------------|------------|
| `/balance [player] [currency|all]` | View balances | `relish.economy.balance` |
| `/bal [player] [currency|all]` | Alias | `relish.economy.balance` |
| `/money [player] [currency|all]` | Alias | `relish.economy.balance` |

### Pay

| Command | Description | Permission |
|--------|-------------|------------|
| `/pay <player> <amount> [currency]` | Send money to a player | `relish.economy.pay` |

### Baltop

| Command | Description | Permission |
|--------|-------------|------------|
| `/baltop [currency] [page]` | Leaderboard | `relish.economy.baltop` |
| `/balancetop [currency] [page]` | Alias | `relish.economy.baltop` |

### Currency

| Command | Description | Permission |
|--------|-------------|------------|
| `/currency list` | List currencies | `relish.economy.currency` |
| `/currency info [currency]` | Currency info | `relish.economy.currency` |

### Exchange

| Command | Description | Permission |
|--------|-------------|------------|
| `/exchange <from> <to> <amount> [confirm]` | Convert currencies | `relish.economy.exchange` |

### Sell (Commands)

| Command | Description | Permission |
|--------|-------------|------------|
| `/sell` | Open sell GUI (Premium) or show help/output | `relish.economy.sell` |
| `/sellhand` | Sell item in hand | `relish.economy.sell` |
| `/sellhotbar` | Sell hotbar items | `relish.economy.sell` |
| `/sellhb` | Alias | `relish.economy.sell` |
| `/sellall [confirm]` | Sell all sellable inventory items | `relish.economy.sell` |

Sell price checking:

| Command | Description | Permission |
|--------|-------------|------------|
| `/sell price <item|@hand|@hotbar|@inv>` | Check sell value | `relish.economy.sell` |
| `/re sell price <item|@hand|@hotbar|@inv>` | Same as above | `relish.economy.sell` |

## Premium Player Features

### Shop GUI

| Command | Description | Permission |
|--------|-------------|------------|
| `/shop` | Open shop GUI | `relish.economy.shop` |
| `/shop help` | Show shop help | `relish.economy.shop` |

### Physical Currency

| Command | Description | Permission |
|--------|-------------|------------|
| `/withdraw <currency> <amount>` | Withdraw as a physical item | `relish.economy.withdraw` |

Deposit interaction is configurable per currency via `currencies.<name>.physical-item.deposit-action` (default: sneak + right-click), if enabled per currency.

### ⭐ Personal Vault (Premium)

Right-click a **Vault block** to open your personal vault. No command needed.

- First-time open: enter a PIN on the keypad GUI (4–16 digits, click numbered heads).
- Subsequent opens: enter your PIN to unlock.
- Inside the vault: place physical currency items in the tray → click **Deposit** to store.
- Use `+/-` buttons to select a withdrawal amount → click **Withdraw** to receive physical items.
- Click the key button to change your PIN at any time.

| Permission | Description | Default |
|------------|-------------|---------|
| `relish.economy.vault.use` | Open the vault | true |

Config: `vault.*` in `config.yml`, GUI layout in `gui.yml` under `vault-gui` and `vault-password-gui`.

Per-currency toggles:
- `currencies.<name>.physical-item.deposit-enabled`
- `currencies.<name>.physical-item.withdraw-enabled`

## Admin Commands

### Core Admin

| Command | Description | Permission |
|--------|-------------|------------|
| `/eco <give|take|set> <player|all|online> <amount> [currency]` | Manage balances | `relish.economy.eco` |
| `/eco clear <player|all|online> [currency]` | Zero out one or all balances (offline-safe) | `relish.economy.eco.clear` |
| `/eco info <player> [currency]` | View balances for any player (offline-safe) | `relish.economy.eco.info` |
| `/re give <player> <vault\|atm> [amount]` | Give vault or ATM block item (bypasses crafting) | `relish.economy.admin` |
| `/re reload` | Reload configuration | `relish.economy.admin` |
| `/re migrate <plugin> <currency>` | Import data from other plugins | `relish.economy.admin` |
| `/re version` | Plugin version/info | `relish.economy.use` |
| `/re help` | Help | `relish.economy.use` |

### Shop Admin (`/re shop ...`)

```text
/re shop help
/re shop search <query>
/re shop price <item>
/re shop remove <item> <category>
```

Shop add / price editor:

```text
/re shop add <item> <category> <buyPrice> [currency]
/re shop add @hand [category] [buyPrice|currency] [customId]
/re shop add @hotbar [category] [currency]
/re shop add @inv [category] [currency]

/re shop setprice <item> [currency]
```

Category management:

```text
/re shop category list
/re shop category create <name> <display name> <icon> <page:slot>
/re shop category enable <name>
/re shop category disable <name>
/re shop category slot <name> <page:slot>
/re shop category remove <name> <item>
```

### Logs

Transaction logs can be viewed from the GUI (Premium) and via the admin command:

| Command | Description | Permission |
|--------|-------------|------------|
| `/re logs [player] [page]` | View transaction history | `relish.economy.logs` |

To view other players' logs, grant:
- `relish.economy.logs.others`

## Amount Shortcuts

You can use these shortcuts anywhere an amount is accepted:

| Shortcut | Value | Example |
|----------|-------|---------|
| `k` | x 1,000 | `5k` = 5,000 |
| `m` | x 1,000,000 | `2m` = 2,000,000 |
| `b` | x 1,000,000,000 | `1b` = 1,000,000,000 |

## Player Disambiguation (Escaping Wildcards)

If a player on your server has a name that conflicts with wildcard selectors (`all`, `online`) or configured currency names (e.g. a player named `dollars`), you can bypass the wildcard/fallback checks and explicitly target that player's account by prefixing their name with `p:` or `player:`.

### Examples:
- `/eco give p:all 100` ➡️ Gives 100 to the player literally named `all` (instead of all players).
- `/eco give p:online 100` ➡️ Gives 100 to the player literally named `online` (instead of online players).
- `/balance p:dollars` ➡️ Views the balance of the player named `dollars` (instead of viewing the sender's dollars currency balance if the target player is offline).
- `/pay p:dollars 50` ➡️ Pays 50 of your default currency to the player named `dollars`.

