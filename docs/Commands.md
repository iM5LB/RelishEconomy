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

Per-currency toggles:
- `currencies.<name>.physical-item.deposit-enabled`
- `currencies.<name>.physical-item.withdraw-enabled`

## Admin Commands

### Core Admin

| Command | Description | Permission |
|--------|-------------|------------|
| `/eco <give|take|set> <player|all> <amount> [currency]` | Manage balances | `relish.economy.eco` |
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
