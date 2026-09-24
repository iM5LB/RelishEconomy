# Physical Currency

Premium feature: withdraw balances as physical items (notes/coins), deposit them back, craft them, and convert natural sources.

![Physical Currency](assets/PhysicalCoin.gif)

## Withdraw & Deposit

| Command / Action | Description |
|------------------|-------------|
| `/withdraw <currency> <amount>` | Withdraw balance as a physical item |
| Sneak + right-click (default) | Deposit a physical currency item |

Deposit behavior is configured per currency:

```yaml
currencies:
  dollars:
    physical-item:
      deposit-enabled: true
      withdraw-enabled: true
      deposit-action:
        enabled: true
        require-sneak: true
        click: RIGHT
      owner-enabled: true
```

## Item Template

Each currency can customize the physical item:

```yaml
physical-item:
  material: PAPER
  value-per-item: 1.0
  name: "<green>$ Dollar Bill"
  lore:
    - "<gray>$ Dollars: {formatted_amount}"
    - "<gray>Owner: <white>{owner}"
  custom-model-data: -1   # >= 0 enables resource-pack models
  glow: false
```

Deposit instruction lore lines are added automatically from language files based on `deposit-action`.

## Natural Sources (Premium)

Convert configured materials into physical currency (smelting, crafting, etc.):

```yaml
physical-item:
  natural-source:
    enabled: true
    match-any-meta: false
    materials:
      GOLD_INGOT: 1.0
      GOLD_BLOCK: 9.0
```

## Crafting

Optional craftable physical currency recipes live under each currency's `crafting:` block. See [Configuration](Configuration.md).

## Next Steps

- [ATM](ATM.md)
- [Personal Vault](PersonalVault.md)
- [Configuration](Configuration.md)
- [Free vs Premium](FreeVsPremium.md)
