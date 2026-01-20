---
layout: default
title: Commands Reference
description: Complete reference for all RelishEconomy commands with examples and usage
permalink: /commands/
---

# Commands Reference

## Player Commands

### Balance Commands
| Command | Description | Permission | Example |
|---------|-------------|------------|---------|
| `/balance [player] [currency]` | Check balance | `relish.economy.balance` | `/bal coins` |
| `/bal [player] [currency]` | Alias for balance | `relish.economy.balance` | `/bal Steve dollars` |
| `/money [player] [currency]` | Alias for balance | `relish.economy.balance` | `/money` |

### Payment Commands
| Command | Description | Permission | Example |
|---------|-------------|------------|---------|
| `/pay <player> <amount> [currency]` | Send money | `relish.economy.pay` | `/pay Steve 100` |

### Leaderboard Commands
| Command | Description | Permission | Example |
|---------|-------------|------------|---------|
| `/baltop [currency] [page]` | View top balances | `relish.economy.baltop` | `/baltop dollars 2` |
| `/balancetop [currency] [page]` | Alias for baltop | `relish.economy.baltop` | `/balancetop` |
| `/topbalances [currency] [page]` | Alias for baltop | `relish.economy.baltop` | `/topbalances coins` |

### Currency Commands
| Command | Description | Permission | Example |
|---------|-------------|------------|---------|
| `/currency list` | List all currencies | `relish.economy.currency` | `/currency list` |
| `/currency info [currency]` | Currency information | `relish.economy.currency` | `/currency info dollars` |
| `/curr list` | Alias for currency | `relish.economy.currency` | `/curr list` |

## Premium Commands ⭐

### Exchange Commands
| Command | Description | Permission | Example |
|---------|-------------|------------|---------|
| `/exchange <from> <to> <amount> [confirm]` | Convert currencies | `relish.economy.exchange` | `/exchange dollars coins 500` |
| `/convert <from> <to> <amount> [confirm]` | Alias for exchange | `relish.economy.exchange` | `/convert coins dollars 10` |
| `/swap <from> <to> <amount> [confirm]` | Alias for exchange | `relish.economy.exchange` | `/swap dollars coins 1000` |

### Shop Commands
| Command | Description | Permission | Example |
|---------|-------------|------------|---------|
| `/shop [category]` | Open shop GUI | `relish.economy.shop` | `/shop blocks` |
| `/store [category]` | Alias for shop | `relish.economy.shop` | `/store` |
| `/buy [category]` | Alias for shop | `relish.economy.shop` | `/buy tools` |

### Selling Commands
| Command | Description | Permission | Example |
|---------|-------------|------------|---------|
| `/sellhand` | Sell item in hand | `relish.economy.sell` | `/sellhand` |
| `/sellall [confirm]` | Sell all items | `relish.economy.sell` | `/sellall confirm` |

### Physical Currency Commands
| Command | Description | Permission | Example |
|---------|-------------|------------|---------|
| `/withdraw <currency> <amount>` | Get physical currency | `relish.economy.withdraw` | `/withdraw coins 10` |

## Admin Commands

### Economy Management
| Command | Description | Permission | Example |
|---------|-------------|------------|---------|
| `/eco give <player\|all> <amount> [currency]` | Give money | `relish.economy.eco` | `/eco give Steve 1000` |
| `/eco take <player\|all> <amount> [currency]` | Take money | `relish.economy.eco` | `/eco take Steve 500` |
| `/eco set <player\|all> <amount> [currency]` | Set balance | `relish.economy.eco` | `/eco set Steve 2000` |
| `/economy give <player> <amount>` | Alias for eco | `relish.economy.eco` | `/economy give Steve 100` |

### Plugin Management
| Command | Description | Permission | Example |
|---------|-------------|------------|---------|
| `/re help [page]` | Show help | `relish.economy.use` | `/re help 2` |
| `/re version` | Plugin information | `relish.economy.use` | `/re version` |
| `/re reload` | Reload configuration | `relish.economy.admin` | `/re reload` |
| `/re license` | Check license status | `relish.economy.admin` | `/re license` |
| `/re migrate <plugin> <currency>` | Import data | `relish.economy.admin` | `/re migrate essentials dollars` |

## Amount Shortcuts

You can use these shortcuts in any amount field:

| Shortcut | Value | Example |
|----------|-------|---------|
| `k` | × 1,000 | `5k` = 5,000 |
| `m` | × 1,000,000 | `2m` = 2,000,000 |
| `b` | × 1,000,000,000 | `1b` = 1,000,000,000 |

## Command Examples

### Basic Usage
```bash
# Check your balance
/balance

# Check someone else's balance in coins
/balance Steve coins

# Send 500 dollars to Steve
/pay Steve 500 dollars

# View top 10 richest players
/baltop

# View page 2 of coin leaderboard
/baltop coins 2
```

### Premium Features
```bash
# Exchange 1000 dollars for coins
/exchange dollars coins 1000 confirm

# Open the shop
/shop

# Sell item in your hand
/sellhand

# Sell all items in inventory
/sellall confirm

# Get 10 physical coins
/withdraw coins 10
```

### Admin Commands
```bash
# Give 1000 dollars to Steve
/eco give Steve 1000 dollars

# Give 500 coins to all online players
/eco give all 500 coins

# Set Steve's balance to 5000 dollars
/eco set Steve 5000 dollars

# Reload plugin configuration
/re reload

# Migrate from EssentialsX
/re migrate essentials dollars
```