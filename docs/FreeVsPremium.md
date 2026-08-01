# Free vs Premium

RelishEconomy ships as one jar. Free features always work. Premium features unlock with a verified `license-key`.

## License Key

In `plugins/RelishEconomy/config.yml`:

```yaml
license-key: "YOUR-KEY-HERE"
```

Then restart or run `/re reload` (admin).

Buy keys from the [M5LB Store](https://m5lb.run.place/?buy=relish-economy). Support: [Discord](https://discord.gg/jDr2KZcGXk).

If verification fails or the key is empty, **free features keep working**. Premium actions show an upgrade message instead of breaking the plugin.

## Free Features

| Area | Included |
|------|----------|
| Balances | `/balance`, `/pay`, `/baltop` |
| Currencies | Multi-currency setup, symbols, colors, starting balances, per-currency permissions |
| Exchange | `/exchange` with per-currency rates |
| Selling | Command selling (`/sellhand`, `/sellhotbar`, `/sellall`) |
| Admin | `/eco` give / take / set / clear / info |
| Storage | SQLite and MySQL |
| Integrations | Vault economy provider, PlaceholderAPI |
| Maintenance | Config updater/validator, backups, migration tools |

## Premium Features

| Feature | What it unlocks |
|---------|-----------------|
| Shop GUI | Categories, paging, search, purchase flow |
| Sell GUI | Drag-and-drop selling, favorites, show unpriced items |
| ATM | Physical currency deposit / withdraw GUI |
| Physical currency | `/withdraw`, shift-deposit, craftable notes/coins, custom model data |
| Natural sources | Convert configured item sources into currency |
| Composter selling | Throw items on a composter to sell |
| Personal Vault | Password-protected currency chest with hologram |
| Block interactions | Shop / sell / ATM blocks |
| Transaction logs | Sell history GUI |

## Next Steps

- [Installation](Installation.md)
- [Configuration](Configuration.md) — `license-key` and currency settings
- [Currencies & Exchange](Currencies.md)
- [Shop System](ShopSystem.md)
- [Sell System](SellSystem.md)
- [Physical Currency](PhysicalCurrency.md)
- [ATM](ATM.md)
- [Personal Vault](PersonalVault.md)
- [Commands](Commands.md)
