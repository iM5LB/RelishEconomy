# Commands

Complete RelishEconomy command reference.

## Player Commands (Free)

### Balance

| Command | Description | Permission |
|---------|-------------|------------|
| `/balance [player] [currency\|all]` | View balances | `relish.economy.balance` |
| `/bal [player] [currency\|all]` | Alias | `relish.economy.balance` |
| `/money [player] [currency\|all]` | Alias | `relish.economy.balance` |

### Pay

| Command | Description | Permission |
|---------|-------------|------------|
| `/pay <player> <amount> [currency]` | Send money to a player | `relish.economy.pay` |

### Baltop

| Command | Description | Permission |
|---------|-------------|------------|
| `/baltop [currency] [page]` | Leaderboard | `relish.economy.baltop` |
| `/balancetop [currency] [page]` | Alias | `relish.economy.baltop` |

### Currency

| Command | Description | Permission |
|---------|-------------|------------|
| `/currency list` | List currencies | `relish.economy.currency` |
| `/currency info [currency]` | Currency info | `relish.economy.currency` |

### Exchange

| Command | Description | Permission |
|---------|-------------|------------|
| `/exchange <from> <to> <amount> [confirm]` | Convert currencies | `relish.economy.exchange` |

### Sell (Commands)

| Command | Description | Permission |
|---------|-------------|------------|
| `/sell` | Open sell GUI (Premium) or show help | `relish.economy.sell` |
| `/sellhand` | Sell item in hand | `relish.economy.sell` |
| `/sellhotbar` | Sell hotbar items | `relish.economy.sell` |
| `/sellhb` | Alias | `relish.economy.sell` |
| `/sellall [confirm]` | Sell all sellable inventory items | `relish.economy.sell` |
| `/sell price <item\|@hand\|@hotbar\|@inv>` | Check sell value | `relish.economy.sell` |

## Premium Player Features

### Shop GUI

| Command | Description | Permission |
|---------|-------------|------------|
| `/shop` | Open shop GUI | `relish.economy.shop` |
| `/shop help` | Show shop help | `relish.economy.shop` |

### Physical Currency

| Command | Description | Permission |
|---------|-------------|------------|
| `/withdraw <currency> <amount>` | Withdraw as a physical item | `relish.economy.withdraw` |

Deposit interaction is configurable per currency via `currencies.<name>.physical-item.deposit-action` (default: sneak + right-click).

### Personal Vault

Right-click a **Vault block** to open your personal vault. No command needed.

- First-time open: enter a PIN on the keypad GUI (4–16 digits).
- Subsequent opens: enter your PIN to unlock.
- Deposit physical currency via the tray; withdraw with `+/-` controls.
- Change PIN with the key button.

| Permission | Description | Default |
|------------|-------------|---------|
| `relish.economy.vault.use` | Open the vault | `true` |

See [Personal Vault](PersonalVault.md) for full details.

## Admin Commands

### Core Admin

| Command | Description | Permission |
|---------|-------------|------------|
| `/eco <give\|take\|set> <player\|all\|online> <amount> [currency]` | Manage balances | `relish.economy.eco` |
| `/eco clear <player\|all\|online> [currency]` | Zero balances (offline-safe) | `relish.economy.eco.clear` |
| `/eco info <player> [currency]` | View balances (offline-safe) | `relish.economy.eco.info` |
| `/re give <player> <vault\|atm> [amount]` | Give vault or ATM block item | `relish.economy.admin` |
| `/re reload` | Reload configuration | `relish.economy.admin` |
| `/re migrate <plugin> <currency>` | Import data from other plugins | `relish.economy.admin` |
| `/re version` | Plugin version/info | `relish.economy.use` |
| `/re help` | Help | `relish.economy.use` |

### Shop Admin

```text
/re shop help
/re shop search <query>
/re shop price <item>
/re shop remove <item> <category>
/re shop add <item> <category> <buyPrice> [currency]
/re shop add @hand [category] [buyPrice|currency] [customId]
/re shop setprice <item> [currency]
/re shop category list
/re shop category create <name> <display name> <icon> <page:slot>
```

### Logs

| Command | Description | Permission |
|---------|-------------|------------|
| `/re logs [player] [page]` | View transaction history | `relish.economy.logs` |

Grant `relish.economy.logs.others` to view other players' logs.

## Amount Shortcuts

| Shortcut | Value | Example |
|----------|-------|---------|
| `k` | x 1,000 | `5k` = 5,000 |
| `m` | x 1,000,000 | `2m` = 2,000,000 |
| `b` | x 1,000,000,000 | `1b` = 1,000,000,000 |

## Player Disambiguation

If a player name conflicts with wildcards (`all`, `online`) or currency names, prefix with `p:` or `player:`:

- `/eco give p:all 100` — player literally named `all`
- `/balance p:dollars` — player named `dollars`
- `/pay p:dollars 50` — pay the player named `dollars`

## Next Steps

- [Permissions](Permissions.md)
- [Shop System](ShopSystem.md)
- [Personal Vault](PersonalVault.md)
