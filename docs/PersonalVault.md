# Personal Vault

Premium feature: a password-protected physical currency chest with PIN keypad and optional hologram.

## Opening

Right-click a **Vault block** to open your personal vault. No command is required.

```yaml
# config.yml
vault:
  enabled: true
  require-sneak: false
  show-hologram: true
```

Admins can give vault items with:

```text
/re give <player> vault [amount]
```

## First-Time Setup

1. Open the vault block.
2. Enter a PIN on the keypad (4–16 digits, numbered player heads).
3. Confirm the PIN.

## Using the Vault

- Place physical currency items in the tray, then click **Deposit**.
- Use `+/-` to choose a withdrawal amount, then click **Withdraw**.
- Click the key button to change your PIN.

| Permission | Description | Default |
|------------|-------------|---------|
| `relish.economy.vault.use` | Open the vault | `true` |

## Hologram

When `vault.show-hologram` is `true`, looking at a vault block (within 5 blocks) shows a floating hologram with stored balances in `{symbol} {name}: {amount}` format.

## GUI & Crafting

- GUI layout: `gui.yml` (`vault-gui`, `vault-password-gui`)
- Crafting recipe and item display: `vault.crafting` / `vault.item-name` in `config.yml`

## Next Steps

- [Physical Currency](PhysicalCurrency.md)
- [ATM](ATM.md)
- [Configuration](Configuration.md)
- [Free vs Premium](FreeVsPremium.md)
