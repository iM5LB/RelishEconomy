# ATM

Premium feature: deposit and withdraw physical currency through a dedicated GUI.

![ATM Overview](assets/ATM-Overview.gif)

## Opening the ATM

Right-click the configured ATM block (sneak required if enabled):

```yaml
# config.yml
atm:
  enabled: true
  block:
    material: LOOM
    require-sneak: true
  deposit:
    manual-confirm: true
```

Admins can give ATM block items with:

```text
/re give <player> atm [amount]
```

## Using the ATM

1. Open the ATM GUI from the block.
2. Place supported physical currency items in the deposit tray.
3. Confirm deposit (when `manual-confirm` is enabled).
4. Select a currency and amount to withdraw as physical items.

Per-currency ATM deposit can be toggled with `physical-item.atm-deposit`.

## Related

Physical notes and coins are covered in [Physical Currency](PhysicalCurrency.md). For long-term password-protected storage, see [Personal Vault](PersonalVault.md).

## Next Steps

- [Physical Currency](PhysicalCurrency.md)
- [Personal Vault](PersonalVault.md)
- [Configuration](Configuration.md)
- [Commands](Commands.md)
