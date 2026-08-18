# Quick Start Guide

Get RelishEconomy up and running in just 5 minutes!

## Prerequisites

Before installing RelishEconomy, make sure you have:

- **Minecraft Server**: Paper 1.21+ (or any Paper fork like Purpur)
- **Java**: Version 21 or higher
- **Optional Plugins**: Vault, PlaceholderAPI (recommended)

## Installation Steps

### 1. Download the Plugin

Choose your version:
- **Free Version**: [Download from Modrinth](https://modrinth.com/plugin/relisheconomy)
- **Premium License**: [Relish Store](https://relishes.studio/product/relisheconomy) to purchase premium access

### 2. Install the Plugin

1. Stop your server
2. Place `RelishEconomy.jar` in your `plugins` folder
3. Start your server
4. The plugin will generate default configuration files

### 3. Basic Configuration

The plugin works out of the box with default settings! But you can customize:

```yaml
# plugins/RelishEconomy/config.yml
currencies:
  dollars:
    symbol: "$"
    display-name: "Dollars"
    color: "<green>"
    default: true
    starting-balance: 100.0
```

### 4. Test the Plugin

Try these commands to verify everything works:

```
/balance - Check your balance
/pay <player> <amount> - Send money to another player
/baltop - View the richest players
```

## First Steps

### For Players

**Check Your Balance**
```
/balance
/bal
```

**Send Money to Friends**
```
/pay PlayerName 100
```

**View Leaderboard**
```
/baltop
```

### For Admins

**Give Money to Players**
```
/eco give PlayerName 1000
/eco give online 1000   # Give 1000 to all online players
/eco give p:iM5LB 1000    # Give 1000 only to player named "iM5LB"
```

**Set Player Balance**
```
/eco set PlayerName 5000
/eco set online 5000    # Set all online players' balance to 5000
/eco set p:iM5LB 5000  # Set player named "iM5LB"'s balance to 5000
```

**Take Money from Players**
```
/eco take PlayerName 500
/eco take online 500    # Take 500 from all online players
```

**Reload Configuration**
```
/re reload
```

## Premium Features Setup

If you purchased a premium license through the Relish Store:

### 1. Add Your License Key

After purchasing from the Relish Store, you'll receive your license key:

```yaml
# config.yml
license-key: "your-license-key-here"
```

> **Note**: Premium source code is not shared. The license key activates premium features in the compiled plugin.

### 2. Enable Shop GUI

```yaml
# config.yml
shop-gui-block: EMERALD_BLOCK  # Right-click emerald blocks to open shop
```

Shop features included in Premium:
- Favorites (`favorites.yml`)
- Purchase GUI flow (quantity selection + confirm/cancel/back)
- Optional "show unpriced items as disabled" toggle (`shop.yml`)

### 3. Enable Sell GUI

```yaml
# config.yml
sell-gui-block: COMPOSTER  # Right-click composters to sell items
composter-selling:
  enabled: true
```

### 4. Configure Item Prices

Edit `prices.yml` to set sell prices:
```yaml
prices:
  DIAMOND: 100.0
  EMERALD: 50.0
  GOLD_INGOT: 25.0
```

### 5. (Optional) Enable Physical Currency Items

RelishEconomy can let players withdraw currency as an item (Premium), and optionally deposit it back:

```yaml
# config.yml (per currency)
currencies:
  coins:
    physical-item:
      material: GOLD_NUGGET
      value-per-item: 1.0
      withdraw-enabled: true
      deposit-enabled: true
      atm-deposit: true
      deposit-action:
        enabled: true
        require-sneak: true
        click: RIGHT
      owner-enabled: true
      custom-model-data: 2001   # set to -1 to disable, or change to match your resource pack model.
```

No extra plugin is required for custom models. Any resource pack can work, as long as it maps your chosen `custom-model-data` to a model.

```text
/withdraw coins 10
```

### 6. (Optional) Setup Personal Vault
RelishEconomy (Premium) lets players set up password-protected vaults to store physical currency items:

```yaml
# config.yml
vault:
  enabled: true
  show-hologram: true          # Show floating balance hologram when looked at
  crafting:
    enabled: true
    amount: 1
    shape:
      - "NNN"
      - "NCN"
      - "NNN"
    ingredients:
      N: NETHERITE_INGOT
      C: CHEST
```

No setup is needed for PIN authentication — the UI automatically prompts players to enter a new PIN on first use.

Commands:
- Give a vault block directly: `/re give <player> vault [amount]` (bypasses crafting)
- Give an ATM block directly: `/re give <player> atm [amount]`

## Resetting Configs (Defaults)

If you delete `plugins/RelishEconomy/` and start the server again, RelishEconomy will recreate the missing files from the bundled defaults.

Notes:
- This is expected to print warnings about recreated/auto-corrected files.
- If you want to fully reset, delete the folder while the server is stopped (not while running).

## Common Issues

### Plugin Not Loading

**Problem**: Plugin shows errors on startup

**Solution**: 
- Check you're using Paper 1.21+ (not Spigot)
- Verify Java 21+ is installed
- Check console for specific error messages

### Commands Not Working

**Problem**: Commands return "Unknown command"

**Solution**:
- Verify plugin is enabled: `/plugins`
- Check for permission issues
- Reload the server

### Database Errors

**Problem**: "Failed to connect to database"

**Solution**:
- For SQLite: Check file permissions
- For MySQL: Verify connection details in config.yml
- Check console logs for specific errors

## Next Steps

Now that you have RelishEconomy installed:

1. **[Configure Currencies](Configuration.md)** - Set up multiple currencies
2. **[Learn Commands](Commands.md)** - Master all available commands
3. **[Setup PlaceholderAPI](PlaceholderAPI.md)** - Add economy info to scoreboards
4. **[Visit Store](https://relishes.studio/product/relisheconomy)** - Purchase premium license keys

## Need Help?

- **Discord**: [Join our support server](https://discord.gg/AdUjAtCsy6)
- **Store**: [Relish Store](https://relishes.studio/product/relisheconomy)
- **Documentation**: [Full documentation](https://relishes.studio/docs/relisheconomy/)
- **Issues**: [Report bugs on GitHub](https://github.com/iM5LB/relisheconomy/issues)
