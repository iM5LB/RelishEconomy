<div align="center">

## Modern economy plugin with multi-currency support

![Relish-Economy-Logo](https://cdn.modrinth.com/data/cached_images/9df4655d0afd67ba097405f931695951fcb513f2_0.webp)

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
- ✅ **Multi-currency system** with custom properties
- ✅ **Currency exchange** with configurable rates
- ✅ **Advanced sell commands** (`/sellhand`, `/sellall`)
- ✅ **Extended baltop features**
- ✅ **Advanced transaction logging**
- ✅ SQLite and MySQL database support
- ✅ Vault integration
- ✅ Multi-language support
- ✅ PlaceholderAPI integration
- ✅ Data migration from other plugins

### ⭐ **Premium Version**
- 🔥 **Shop GUI** with category browsing
- 🔥 **Sell GUI** for item selling
- 🔥 **Block interactions** (shop/sell blocks)
- 🔥 **GUI customization** and interactions
- 🔥 **Physical currency withdrawal**
- 🔥 **Composter selling** - Right-click composter to sell items

---

## 📦 **Installation**

1. **Download** the plugin JAR file
2. **Place** it in your server's `plugins` folder
3. **Start/Restart** your server
4. **(Optional)** For premium features, open a ticket in [Discord](https://discord.gg/hjKcHavRjT) to get license key
5. **Place license key** in `config.yml`
6. **Reload** the plugin

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
| `/exchange <from> <to> <amount>` | Convert currencies | `/exchange dollars coins 500` |
| `/shop [subcommands]` ⭐ | Open shop GUI | `/shop blocks` 
`/sell [subcommands]` ⭐ | Open sell  GUI | `/sell price` |
| `/sellhand` | Sell item in hand | `/sellhand` |
| `/sellall` | Sell all items | `/sellall confirm` |
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

## 🛒 **Shop System** ⭐

### 📦 **Shop Features**
RelishEconomy's premium shop system provides a comprehensive item marketplace with intuitive GUI interfaces and flexible configuration options.

**Core Shop Capabilities:**
- **15+ item categories** - Wood, Stone, Deepslate, Bricks, Sand, Colors, Natural, Glass, Lighting, Decorations, etc.
- **Dynamic pricing** - Buy prices calculated from sell prices with configurable multiplier
- **Category management** - Enable/disable categories, set custom icons
- **Multi-currency support** - Accept payments in configured buy currency
- **Bulk purchasing** - Buy items in quantities of 1, 32, or 64 with one click
- **Permission integration** - Works with permission plugins for access control

**Shop GUI Interface:**
- **Category browser** - Navigate through 15+ organized item categories
- **Item preview** - See item details and buy prices
- **Balance display** - Real-time balance updates during shopping
- **Sound effects** - Audio feedback for purchases and navigation
- **Pagination** - Navigate through multiple pages of items
- **Search functionality** - Find items across all categories


<div align="center">

## 🔍 Search functionality 
![Shop Search](https://cdn.modrinth.com/data/cached_images/d2b246b0fa32ce809829b3fa9d5780be933ae7e2.png)

## 🗂️ 15+ of Categories
![Shop Menu](https://cdn.modrinth.com/data/cached_images/e305729593d7ad061b930e4ff76b86789c74d6c5.png)

</div>

### 🏪 **Shop Configuration**
```yaml
# shop.yml
shop:
  buy-currency: "dollars"
  buy-multiplier: 2.0
  gui:
    title: "<#fdb833>RelishShop"
    items-per-page: 28

categories:
  wood:
    display-name: "Wood"
    icon: OAK_LOG
    enabled: true
    slot: "1:0"
    items:
      - OAK_LOG
      - SPRUCE_LOG
      - OAK_PLANKS
      - SPRUCE_PLANKS
      # ... more items
  
  stone:
    display-name: "Stone"
    icon: STONE
    enabled: true
    slot: "1:1"
    items:
      - STONE
      - COBBLESTONE
      - STONE_BRICKS
      # ... more items
```

**Available Categories:**
- **Wood** - All wood types, logs, planks, stripped variants
- **Stone** - Stone, cobblestone, variants
- **Deepslate** - Deepslate blocks and variants  
- **Bricks** - All brick types and variants
- **Sand/Sandstone** - Sand, sandstone, variants
- **Color Blocks** - Wool, concrete, terracotta, glass
- **Natural Blocks** - Dirt, grass, leaves, flowers
- **Glass** - All glass types and panes
- **Lighting** - Torches, lanterns, glowstone
- **Decorations** - Decorative blocks and items

### 🎯 **Shop Commands**
```bash
/shop                    # Open main shop interface
/shop [category]         # Open specific category directly
```

---

## 💰 **Sell System**

### 📤 **Sell Features**
The sell system provides multiple ways for players to convert their items into currency, from quick command-based selling to an interactive GUI interface.

**Sell Methods:**
- **Command-based selling** - Quick `/sellhand` and `/sellall` commands (Free)
- **Interactive Sell GUI** - Drag-and-drop interface for selective selling (Premium)
- **Auto-grab functionality** - Automatically collect sellable items from inventory
- **Price calculation** - Real-time value calculation with currency conversion
- **Confirmation system** - Prevent accidental sales with confirmation prompts

**Advanced Sell Features:**
- **Multi-currency payouts** - Receive payment in configured target currency
- **Bulk selling** - Sell entire stacks or inventory contents at once
- **500+ sellable items** - Comprehensive item price database
- **Composter selling** - Throw items on composter for instant selling (Premium)
- **Transaction logging** - Track all sell transactions for auditing

### 🎮 **Sell Commands (Free)**
```bash
/sellhand               # Sell the item in your hand
/sellall                # Sell all sellable items in inventory
/sellall confirm        # Confirm bulk selling with safety check
```

### 🖱️ **Sell GUI Interface** ⭐
The premium Sell GUI provides an intuitive drag-and-drop interface for item selling:

**GUI Features:**
- **Drag-and-drop zones** - Simply drag items to sell them
- **Quick grab button** - Auto-collect all sellable items from inventory
- **Real-time pricing** - See total sale value update as you add items
- **Total calculator** - View total sale value before confirming
- **Confirmation system** - Confirm sale with total summary
- **Sound effects** - Audio feedback for all interactions

<div align="center">

### 👌 Total values calculator
![Sell GUI](https://cdn.modrinth.com/data/cached_images/98a22983dc91b06672ef74eb6450c8d0ed56da10.png)

### 🪝 Grab all sellable items by one click
![Sell GUI](https://cdn.modrinth.com/data/cached_images/622d08d604dad3ae3d74c40ce34441f0f5b0fea3.png)

</div>

### ⚙️ **Sell Configuration**
```yaml
# prices.yml
target-currency: "dollars"

prices:
  # Basic format
  STONE: 0.5
  COBBLESTONE: 0.3
  OAK_LOG: 1.5
  
  # Multi-currency format (if needed)
  DIAMOND: { price: 100, currency: "gems" }
  EMERALD: { price: 150, currency: "tokens" }
```

**500+ Sellable Items Including:**
- **Stone variants** - Stone, cobblestone, bricks, deepslate
- **Wood materials** - All logs, planks, stripped variants
- **Natural blocks** - Dirt, sand, gravel, clay
- **Precious materials** - Diamonds, emeralds, gold, iron
- **Nether materials** - Netherrack, soul sand, nether bricks
- **End materials** - End stone, purpur blocks
- **Mob drops** - Bones, string, gunpowder, leather
- **Food items** - Wheat, carrots, potatoes, meat

### 🔧 **Sell Block Interactions** ⭐
Premium users can use physical blocks for convenient item selling:

**Sell Block Features:**
- **Right-click COMPOSTER** - Opens sell GUI interface
- **Composter item selling** - Throw items on composter to sell instantly
- **Configurable cooldown** - Prevents spam (500ms default)
- **Visual/audio feedback** - Confirmation messages and sounds

```yaml
# config.yml
composter-selling:
  enabled: true
  cooldown: 500

sell-gui-block: COMPOSTER
shop-gui-block: EMERALD_BLOCK
```

<div align="center">

## ✨ Easy to use
![Relish-Economy-ShopGUI.gif](https://cdn.modrinth.com/data/5RyYvL8C/images/d2f7081e7bac65fea442a276562fb537b6422563.gif)

</div>


## 🎨 **GUI Features** ⭐

### 🛒 **Shop Interface**
The premium shop GUI provides an elegant and user-friendly shopping experience with full customization options.

**Interface Highlights:**
- **Category browsing** with configurable icons and colors
- **Item purchasing** with multiple quantity options (1, 32, 64)
- **Balance display** with real-time updates
- **Sound effects** for all interactions
- **Configurable GUI size** and layout options
- **Permission-based category access**
  

### 💼 **Sell Interface**
The premium sell GUI offers an intuitive drag-and-drop experience for item selling.

**Interface Features:**
- **Drag-and-drop** item selling with visual feedback
- **Quick grab** button to auto-collect sellable items
- **Real-time value** calculation and display
- **Confirmation system** with total sale summary
- **Sound effects** and particle animations
- **Multi-currency** payout options

<div align="center">

![Relish-Economy-SellGUI.gif](https://cdn.modrinth.com/data/5RyYvL8C/images/a1244aaf472b1276888f99278b0e4da431bf892c.gif)

</div>

### 🎛️ **GUI Customization** ⭐
Premium users have full control over GUI appearance and behavior:

**Customization Options:**
- **GUI sizes** - Choose from 9, 18, 27, 36, 45, or 54 slot layouts
- **Custom titles** - Set personalized GUI titles with color codes
- **Item icons** - Use any material as category or button icons
- **Sound effects** - Configure custom sounds for different actions
- **Layout templates** - Pre-designed layouts or create your own
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

![relisheconomy scoreboard](https://cdn.modrinth.com/data/cached_images/d13ba1e7213dd18a81d28f1a6dfdabff2a63b9f6_0.webp)

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

## 🚀 **Upcoming Features**

We're constantly working to improve RelishEconomy with exciting new features:

### 🤝 **Player-to-Player Trading**
A secure and intuitive trading system for direct player interactions:
- **Secure trade interface** with dual confirmation system
- **Trade history and logging** for all transactions
- **Configurable trade limits** to prevent abuse
- **Trade cooldowns** with customizable durations
- **Item and currency trading** in a single interface
- **Permission-based restrictions** for controlled access

### 🏛️ **Auction House System**
A server-wide marketplace for buying and selling items:
- **List items for auction** with custom prices and durations
- **Bid on items** from other players with competitive bidding
- **Automatic payment and item delivery** upon auction completion
- **Auction expiration and refund system** for unsold items
- **Search and filter functionality** to find specific items
- **Multi-currency support** for flexible pricing
- **Auction history tracking** for buyers and sellers
- **Category-based browsing** similar to shop system

---

## 📞 **Support & Links**

<div align="center">

[![Discord](https://img.shields.io/badge/Discord-Support-7289da?style=for-the-badge&logo=discord)](https://discord.gg/hjKcHavRjT)
[![Documentation](https://img.shields.io/badge/Docs-Read-blue?style=for-the-badge&logo=gitbook)](https://im5lb.github.io/relisheconomy)
[![Issues](https://img.shields.io/badge/🐛%20Issues-Report-orange?style=for-the-badge)](https://github.com/iM5LB/relisheconomy/issues)
[![Premium](https://img.shields.io/badge/Premium-Contact-gold?style=for-the-badge&logo=discord)](https://discord.gg/hjKcHavRjT)
[![Donate](https://img.shields.io/badge/💖%20Donate-Love-ff69b4?style=for-the-badge)](https://creators.sa/m5lb)
</div>

---

## 📄 **License**

**RelishEconomy is proprietary software. All rights reserved.**

### License Types

#### 🆓 Free Version
- Available without license key
- Basic economy features included
- May be used on unlimited servers
- **NOT open source** - modification and redistribution prohibited

#### ⭐ Premium Version
- Requires valid license key from M5LB
- Includes all premium features (Shop GUI, Sell GUI, Physical Currency, etc.)
- License key tied to purchaser and server count
- **NOT open source** - modification and redistribution prohibited

For full license terms, see [LICENSE](LICENSE) file.

### Obtain Premium License

To get a premium license key:
- 🎫 **Open a ticket in [Discord](https://discord.gg/hjKcHavRjT)**

---
<div align="center">

**Made with ❤️ by M5LB**

</div>
