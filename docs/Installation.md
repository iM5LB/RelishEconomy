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

### 1. Download the Plugin
- **Free Version**: Download from [Modrinth](https://modrinth.com/plugin/relish-economy)
- **Premium Version**: Purchase from [BuiltByBit](https://builtbybit.com/resources/relishecoonomy.90571/)

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
3. Reload the plugin
4. Run `/re reload` to verify activation

## Troubleshooting

### Common Issues
- **Plugin not loading**: Check Java version (requires 21+)
- **Commands not working**: Verify Vault is installed
- **Database errors**: Check file permissions

### Getting Help
- Join our [Discord](https://discord.gg/jDr2KZcGXk)
- Report bugs on [GitHub](https://github.com/iM5LB/relisheconomy/issues)
