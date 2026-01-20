---
layout: default
title: Installation Guide
description: Step-by-step guide to install and set up RelishEconomy on your Minecraft server
permalink: /installation/
---

# Installation Guide

Get RelishEconomy up and running on your Minecraft server in just a few minutes.

## Requirements

| Component | Requirement | Notes |
|-----------|-------------|-------|
| **Minecraft** | 1.21+ | Latest version recommended |
| **Server** | Paper, Purpur, or Paper-based forks | Spigot not officially supported |
| **Java** | 21+ | Required for Minecraft 1.21+ |
| **Dependencies** | Vault (recommended), PlaceholderAPI (optional) | Auto-detected if present |

## Step-by-Step Installation

### Step 1: Download the Plugin

**Free Version** - Perfect for basic economy needs
- Multi-currency support
- Basic commands  
- Vault integration
- SQLite database

[Download from Modrinth](https://modrinth.com/plugin/relisheconomy)

**Premium Version** <span class="badge badge-premium">Premium</span> - Advanced features for professional servers
- Shop & Sell GUIs
- Currency exchange
- MySQL support
- Premium support

[Purchase on BuiltByBit](https://builtbybit.com/resources/relisheconomy)

### Step 2: Install Dependencies (Recommended)

**Vault** (Highly Recommended)
- Enables compatibility with other economy plugins
- Download: [Spigot](https://www.spigotmc.org/resources/vault.34315/)

**PlaceholderAPI** (Optional)  
- Adds placeholder support for scoreboards and chat
- Download: [Spigot](https://www.spigotmc.org/resources/placeholderapi.6245/)

### Step 3: Server Installation

1. **Stop your server** (important for clean installation)

2. **Place the JAR file** in your `plugins/` folder:
   ```
   server/
   ├── plugins/
   │   ├── RelishEconomy.jar  ← Place here
   │   ├── Vault.jar
   │   └── PlaceholderAPI.jar
   └── ...
   ```

3. **Start your server** - RelishEconomy will create default configuration files

### Step 4: First-Time Setup

After installation, you'll find these files in `plugins/RelishEconomy/`:

| File | Purpose | Required |
|------|---------|----------|
| `config.yml` | Main configuration | ✅ Yes |
| `lang/en.yml` | English messages | ✅ Yes |
| `lang/ar.yml` | Arabic messages | ❌ Optional |
| `prices.yml` | Item prices for selling <span class="badge badge-premium">Premium</span> | ❌ Optional |
| `shop.yml` | Shop configuration <span class="badge badge-premium">Premium</span> | ❌ Optional |
| `gui.yml` | GUI customization <span class="badge badge-premium">Premium</span> | ❌ Optional |

### Step 5: Basic Configuration

Edit `config.yml` to set up your first currency:

```yaml
currencies:
  dollars:
    symbol: "$"
    display-name: "Dollars"
    color: "<green>"
    default: true
    starting-balance: 100.0
    payments-enabled: true
```

### Step 6: Restart and Test

1. **Restart your server** to apply configuration changes

2. **Verify installation** with these commands:
   ```
   /re version          # Check plugin status
   /balance             # Test basic functionality
   /re help             # View available commands
   ```

## Premium Activation

If you purchased the premium version:

1. **Get your license key** from your BuiltByBit purchase

2. **Add it to config.yml**:
   ```yaml
   license-key: "your-license-key-here"
   ```

3. **Restart server** and verify with:
   ```
   /re license          # Check license status
   ```

## Troubleshooting

### Common Issues

**Plugin not loading**
- Check Java version (requires 21+)
- Verify server software (Paper/Purpur required)
- Check console for error messages

**Commands not working**
- Ensure Vault is installed and loaded
- Check permissions are set correctly
- Verify plugin loaded successfully

**Database errors**
- Check file permissions in plugins folder
- For MySQL: verify connection details
- Check available disk space

### Getting Help

- [Discord Support](https://discord.gg/relish)
- [Report Issues](https://github.com/iM5LB/relisheconomy/issues)

## Next Steps

Once RelishEconomy is installed:

1. **[Configure currencies]({{ "/configuration/" | relative_url }})** - Set up your server's economy
2. **[Learn commands]({{ "/commands/" | relative_url }})** - Master all available commands  
3. **[Set up PlaceholderAPI]({{ "/placeholderapi/" | relative_url }})** - Integrate with other plugins

## Requirements

| Component | Requirement |
|-----------|-------------|
| **Minecraft** | 1.21+ |
| **Server** | Paper, Purpur, or Paper-based forks |
| **Java** | 21+ |
| **Dependencies** | Vault (recommended), PlaceholderAPI (optional) |

## Step-by-Step Installation

### 1. Download the Plugin
- **Free Version**: Download from [Modrinth](https://modrinth.com/plugin/relisheconomy)
- **Premium Version**: Purchase from [BuiltByBit](https://builtbybit.com/resources/relisheconomy)

### 2. Install Dependencies
Download and install these plugins (optional but recommended):
- [Vault](https://www.spigotmc.org/resources/vault.34315/) - For economy integration
- [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) - For placeholders

### 3. Server Installation
1. Stop your server
2. Place `RelishEconomy.jar` in your `plugins/` folder
3. Start your server
4. The plugin will create default configuration files

### 4. First-Time Setup
After installation, you'll find these files in `plugins/RelishEconomy/`:
- `config.yml` - Main configuration
- `lang/en.yml` - English messages
- `lang/ar.yml` - Arabic messages
- `prices.yml` - Item prices for selling (Premium)
- `shop.yml` - Shop configuration (Premium)
- `gui.yml` - GUI customization (Premium)

### 5. Basic Configuration
Edit `config.yml` to set up your currencies:

```yaml
currencies:
  dollars:
    symbol: "$"
    display-name: "Dollars"
    color: "<green>"
    default: true
    starting-balance: 100.0
```

### 6. Restart and Test
1. Restart your server
2. Run `/re version` to verify installation
3. Test with `/balance` command

## Premium Activation

If you purchased the premium version:
1. Get your license key from BuiltByBit
2. Add it to `config.yml`:
```yaml
license-key: "your-license-key-here"
```
3. Restart server
4. Run `/re license` to verify activation

## Troubleshooting

### Common Issues
- **Plugin not loading**: Check Java version (requires 21+)
- **Commands not working**: Verify Vault is installed
- **Database errors**: Check file permissions

### Getting Help
- Check the [Troubleshooting Guide](Troubleshooting)
- Join our [Discord](https://discord.gg/relish)
- Report bugs on [GitHub](https://github.com/RelishDev/RelishEconomy/issues)