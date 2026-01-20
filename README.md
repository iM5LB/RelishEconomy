<div align="center">
  
[![License](https://img.shields.io/badge/License-Premium-gold.svg)](https://builtbybit.com/resources/relisheconomy)
[![Version](https://img.shields.io/badge/Version-1.0-blue.svg)](https://github.com/RelishDev/RelishEconomy)
[![Minecraft](https://img.shields.io/badge/Minecraft-1.21+-green.svg)](https://papermc.io)
[![Java](https://img.shields.io/badge/Java-21+-orange.svg)](https://adoptium.net)



![Relish-Economy-Logo](https://cdn.modrinth.com/data/cached_images/7cde857e8cafd9f53e73608b7d66ae763fcc6015_0.webp)

**Modern economy plugin with multi-currency support**

</div>

---

## 🌟 **Why Choose RelishEconomy?**

RelishEconomy provides a solid economy foundation with multi-currency support, database flexibility, and seamless plugin integrations. Built for modern Minecraft servers with performance and reliability in mind.

### ✨ **Key Highlights**

🏦 **Multi-Currency System** - Support for multiple custom currencies  
🚀 **High Performance** - Advanced caching with Caffeine for fast operations  
🔧 **Full Integration** - Vault and PlaceholderAPI support  
🗄️ **Database Flexibility** - SQLite and MySQL support  
🌍 **Multi-Language** - Built-in English and Arabic translations  

---

## 📋 **Requirements**

| Component | Requirement |
|-----------|-------------|
| **Minecraft** | 1.21+ |
| **Server** | Paper, Purpur, or Paper-based forks |
| **Java** | 21+ |
| **Soft Dependencies** | Vault (recommended), PlaceholderAPI (optional) |

---

## 🚀 **Features Overview**

### 🆓 **Free Version**
- ✅ Basic economy commands (`/balance`, `/pay`, `/baltop`)
- ✅ Single currency support
- ✅ SQLite database
- ✅ Vault integration
- ✅ Multi-language support
- ✅ PlaceholderAPI integration
- ✅ Data migration from other plugins

### ⭐ **Premium Version**
- 🔥 **Multi-currency system** with custom properties
- 🔥 **Currency exchange** with configurable rates
- 🔥 **Shop GUI** with category browsing
- 🔥 **Sell GUI** for item selling
- 🔥 **MySQL support** for large networks
- 🔥 **Advanced sell commands** (/sellhand, /sellall)
- 🔥 **Physical currency withdrawal**
- 🔥 **Extended baltop features**

---

## 📦 **Installation**

1. **Download** the plugin JAR file
2. **Place** it in your server's `plugins` folder
3. **Start/Restart** your server
4. **Configure** in `plugins/RelishEconomy/config.yml`
5. **Get premium** from [BuiltByBit](https://builtbybit.com/resources/relisheconomy) for advanced features

```bash
# Quick setup commands
/re help          # View all commands
/re version       # Check plugin status
/re reload        # Reload configuration
```

---

## 🎮 **Commands & Usage**

### 👤 **Player Commands**

| Command | Description | Example |
|---------|-------------|---------|
| `/balance [player] [currency]` | Check balance | `/bal coins` |
| `/pay <player> <amount>` | Send money | `/pay Steve 100` |
| `/baltop [currency] [page]` | View leaderboard | `/baltop dollars 2` |
| `/currency <list\|info>` | View currencies | `/currency list` |
| `/exchange <from> <to> <amount>` ⭐ | Convert currencies | `/exchange dollars coins 500` |
| `/shop [category]` ⭐ | Open shop GUI | `/shop blocks` |
| `/sellhand` ⭐ | Sell item in hand | `/sellhand` |
| `/sellall` ⭐ | Sell all items | `/sellall confirm` |
| `/withdraw <currency> <amount>` ⭐ | Get physical currency | `/withdraw coins 10` |

### 👑 **Admin Commands**

| Command | Description | Example |
|---------|-------------|---------|
| `/eco <give\|take\|set> <player> <amount>` | Manage balances | `/eco give Steve 1000` |
| `/re reload` | Reload configuration | `/re reload` |
| `/re migrate <plugin> <currency>` | Import from other plugins | `/re migrate essentials dollars` |

### 💡 **Amount Shortcuts**
- `k` = thousand (e.g., `5k` = 5,000)
- `m` = million (e.g., `2m` = 2,000,000)  
- `b` = billion (e.g., `1b` = 1,000,000,000)

---

## 🔧 **Configuration**

### 💰 **Currency Setup**
```yaml
currencies:
  dollars:
    symbol: "$"
    display-name: "Dollars"
    color: "<green>"
    default: true
    starting-balance: 100.0
    payments-enabled: true
    
  coins:
    symbol: "◎"
    display-name: "Coins"
    color: "<gold>"
    starting-balance: 50.0
    payments-enabled: true
```

### 🗄️ **Database Options**
```yaml
database:
  type: sqlite  # or mysql for networks
  
  mysql:
    host: localhost
    port: 3306
    database: relisheconomy
    username: root
    password: password
```

### 🔄 **Currency Exchange** ⭐
```yaml
exchange-rates:
  dollars:
    coins: 0.01  # 1 dollar = 0.01 coins
  coins:
    dollars: 100  # 1 coin = 100 dollars
```

### 🔄 **Data Migration**

RelishEconomy can import data from other economy plugins:

**Supported Plugins:**
- **EssentialsX** - Import from userdata files
- **CMI** - Import from SQLite database
- **TokenManager** - Import token balances
- **PlayerPoints** - Import point balances
- **CoinsAPI** - Import coin balances
- **GemsEconomy** - Import gem balances


**Migration Features:**
- ✅ **Automatic detection** of source plugin data
- ✅ **UUID conversion** for modern Minecraft
- ✅ **Offline player support** - migrates all accounts
- ✅ **Progress tracking** with detailed reports
- ✅ **Async processing** - no server lag

---

## 🎨 **GUI Features** ⭐

### 🛒 **Shop Interface**
- **Category browsing** with configurable icons
- **Item purchasing** with multiple quantity options (1, 32, 64)
- **Balance display** and navigation
- **Sound effects** for interactions
- **Configurable GUI size** and layout

### 💼 **Sell Interface**
- **Drag-and-drop** item selling
- **Quick grab** button to auto-collect sellable items
- **Real-time value** calculation
- **Confirmation system** with total display
- **Sound effects** and visual feedback

---

## 🔌 **Integrations**

### 🏛️ **Vault API**
Full economy provider implementation:
- `getBalance()`, `depositPlayer()`, `withdrawPlayer()`
- Compatible with **any plugin** using Vault
- Multi-currency support through Vault

### 📊 **PlaceholderAPI Integration**

**Balance Placeholders:**
```
%relisheconomy_balance_[currency]%        # Raw balance (e.g. 1000.50)
%relisheconomy_formatted_[currency]%      # Formatted balance (e.g. $1,000.50)
```

**Leaderboard Placeholders:**
```
%relisheconomy_baltop_[position]_[currency]_name%     # Player name at position
%relisheconomy_baltop_[position]_[currency]_balance%  # Formatted balance at position
%relisheconomy_baltop_[position]_[currency]_raw%      # Raw balance at position
%relisheconomy_rank_[currency]%                       # Player's rank
```

**Currency Information:**
```
%relisheconomy_currency_[currency]_symbol%       # Currency symbol
%relisheconomy_currency_[currency]_display%      # Display name
%relisheconomy_currency_[currency]_starting%     # Starting balance
%relisheconomy_currency_[currency]_default%      # Is default currency
```

**Utility Placeholders:**
```
%relisheconomy_hasenough_[amount]_[currency]%    # true/false if player has enough
%relisheconomy_exchangerate_[from]_[to]%         # Exchange rate between currencies
```

**Server Statistics:**
```
%relisheconomy_stats_currencies%    # Number of currencies
%relisheconomy_stats_accounts%      # Number of cached accounts
%relisheconomy_stats_dbtype%        # Database type (sqlite/mysql)
%relisheconomy_stats_dbhealthy%     # Database health status
```

---

## 🌍 **Multi-Language Support**

### 🗣️ **Built-in Languages**
- 🇺🇸 **English** (en) - Complete
- 🇸🇦 **Arabic** (ar) - Complete with RTL support

### 🌐 **Custom Languages**
Create `lang/[code].yml` files for any language:
```yaml
# Example: lang/es.yml for Spanish
balance:
  current: "<green>Tu saldo: {balance}"
  other: "<green>Saldo de {player}: {balance}"
```

---

## 📈 **Performance & Scalability**

### ⚡ **Optimization Features**
- **Caffeine caching** for instant data access
- **Connection pooling** with HikariCP (MySQL)
- **Async operations** for database queries
- **Baltop caching** with configurable duration
- **Auto-cleanup** of stale cache data

### 📊 **Scalability Options**
- **SQLite** for small-medium servers (0-500 players)
- **MySQL** for large networks (500+ players)
- **Real-time sync mode** for external integrations
- **Database health monitoring**

---

## 📞 **Support & Links**

<div align="center">

[![Discord](https://img.shields.io/badge/Discord-Support-7289da?style=for-the-badge&logo=discord)](https://discord.gg/MYA5tYKXsY)
[![Documentation](https://img.shields.io/badge/Docs-Read-blue?style=for-the-badge&logo=gitbook)](https://im5lb.github.io/relisheconomy)
[![Premium](https://img.shields.io/badge/Premium-Buy-gold?style=for-the-badge&logo=paypal)](https://builtbybit.com/resources/relisheconomy)
[![GitHub](https://img.shields.io/badge/GitHub-Source-black?style=for-the-badge&logo=github)](https://github.com/im5lb/RelishEconomy)
</div>

---

## 📄 **License**

RelishEconomy is available in two versions:
- **Free Version**: Basic economy features
- **Premium Version**: Advanced features and GUIs

For premium licensing, visit [BuiltByBit](https://builtbybit.com/resources/relisheconomy).

---

<div align="center">

**Made with ❤️ by the Relish Development Team**

</div>
