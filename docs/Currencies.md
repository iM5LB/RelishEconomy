# Currencies & Exchange

RelishEconomy supports multiple currencies with per-currency formatting, permissions, and exchange rates.

## Overview

Each currency can define:
- Symbol, display name, and MiniMessage color
- Starting balance and default currency flag
- Payment toggles and permission gates
- Decimal precision
- Exchange rates to other currencies
- Physical item templates (Premium — see [Physical Currency](PhysicalCurrency.md))

Configure under `currencies:` in `config.yml`. Full reference: [Configuration](Configuration.md).

## Player Commands

| Command | Description |
|---------|-------------|
| `/currency list` | List currencies |
| `/currency info [currency]` | Currency details |
| `/balance [player] [currency\|all]` | View balances |
| `/pay <player> <amount> [currency]` | Send money |
| `/baltop [currency] [page]` | Leaderboard |
| `/exchange <from> <to> <amount> [confirm]` | Convert currencies |

## Exchange

Rates are defined per currency:

```yaml
exchange-fee-percentage: 2.5
currencies:
  dollars:
    exchange-rates:
      coins: 0.01
  coins:
    exchange-rates:
      dollars: 100.0
    exchange-enabled: true
```

Use `exchange-enabled: false` on a currency to disable `/exchange` for that currency.

## Next Steps

- [Configuration](Configuration.md)
- [Physical Currency](PhysicalCurrency.md)
- [PlaceholderAPI](PlaceholderAPI.md)
- [Commands](Commands.md)
