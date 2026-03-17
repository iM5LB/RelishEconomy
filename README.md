<div align="center">

## 💰 Multi-Currency Economy • Shop • Sell GUI • Physical Currency

![Relish-Economy-Logo](https://cdn.modrinth.com/data/cached_images/9df4655d0afd67ba097405f931695951fcb513f2_0.webp)
[![M5LB Store Banner](docs/assets/M5LBStore.png)](https://m5lb.run.place/)
[![Discord](https://img.shields.io/badge/Discord-Support-7289da?style=for-the-badge&logo=discord)](https://discord.gg/hjKcHavRjT)
[![Documentation](https://img.shields.io/badge/Docs-Read-blue?style=for-the-badge&logo=gitbook)](https://im5lb.github.io/relisheconomy)
[![Issues](https://img.shields.io/badge/🐛%20Issues-Report-orange?style=for-the-badge)](https://github.com/iM5LB/relisheconomy/issues)
[![Store](https://img.shields.io/badge/Store-License%20Keys-gold?style=for-the-badge)](https://m5lb.run.place/)
[![Donate](https://img.shields.io/badge/💖%20Donate-Love-ff69b4?style=for-the-badge)](https://creators.sa/m5lb)

</div>

---

## 🌟 **Why Choose RelishEconomy?**

RelishEconomy provides a solid economy foundation with multi-currency support, database flexibility, and seamless plugin integrations. Built for modern Minecraft servers with performance and reliability in mind.

### ✨ **Key Highlights**

🏦 **Multi-Currency System** - Support for multiple custom currencies  
🚀 **High Performance** - Advanced caching with Caffeine for fast operations  
🔧 **Full Integration** - Vault and PlaceholderAPI support  
🗄️ **Database Flexibility** - SQLite and MySQL support  
🌍 **Multi-Language** - Built-in English, Arabic, and Portuguese translations  

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
- ✅ Basic economy commands (`/balance`, `/pay`, `/baltop`, `/eco`)
- ✅ **Multi-currency system** with custom properties
- ✅ Per-currency formatting, permissions, and decimal control
- ✅ **Currency exchange** with per-currency exchange rates
- ✅ Command-based selling (`/sellhand`, `/sellhotbar`, `/sellall`)
- ✅ Sold-item hover breakdowns for sell commands
- ✅ Baltop leaderboard placeholders and balance placeholders
- ✅ Data migration from other plugins
- ✅ Player username storage alongside UUID balances
- ✅ Towny and Vault economy compatibility
- ✅ Vault and PlaceholderAPI support
- ✅ SQLite and MySQL support
- ✅ Config validation, backup, and auto-recovery for bundled files

### ⭐ **Premium Version**
- ⭐ **Shop GUI** with category browsing
- ⭐ **Sell GUI** for item selling
- ⭐ **Block interactions** (shop/sell blocks)
- ⭐ **GUI customization** and interactions
- ⭐ **Physical currency withdraw and shift-deposit**
- ⭐ **Craftable physical currency with owner metadata**
- ⭐ **Composter selling** - throw items on composter to sell them



---

## 📦 **Installation**

1. **Download** the plugin JAR file
2. **Place** it in your server's `plugins` folder
3. **Start/Restart** your server
4. **(Optional)** For premium features, buy a license key from [M5LB Store](https://m5lb.run.place/)
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
| `/shop` ⭐ | Open shop GUI | `/shop` |
| `/shop help` ⭐ | Show shop help | `/shop help` |
| `/sell [subcommands]` ⭐ | Open sell GUI | `/sell price` |
| `/sellhand` | Sell item in hand | `/sellhand` |
| `/sellhotbar` | Sell hotbar items | `/sellhotbar` |
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

### **Currency Setup**
```yaml
currencies:
  dollars:
    name: "dollars"
    symbol: "$"
    display-name: "Dollars"
    color: "<green>"
    default: true
    starting-balance: 100.0
    payments-enabled: true
    permission: ""
    decimals-enabled: true
    exchange-rates:
      coins: 0.01
    physical-item:
      material: PAPER
      deposit-enabled: true
      withdraw-enabled: true
      name: "<green><bold>Dollar Bill"
      lore:
        - "<gray>Value: {formatted_amount}"
        - "<gray>Owner: <white>{owner}"
        - ""
        - "<yellow>Shift + Right-Click to deposit"
    crafting:
      enabled: false
      value: 100.0
      amount: 1

  coins:
    name: "coins"
    symbol: "◎"
    display-name: "Coins"
    color: "<gold>"
    default: false
    starting-balance: 50.0
    payments-enabled: true
    permission: ""
    decimals-enabled: false
    exchange-rates:
      dollars: 100.0
    physical-item:
      material: GOLD_NUGGET
      deposit-enabled: true
      withdraw-enabled: true
      name: "<gold><bold>Gold Coin"
      lore:
        - "<gray>Value: {formatted_amount}"
        - "<gray>Owner: <white>{owner}"
        - ""
        - "<yellow>Shift + Right-Click to deposit"
    crafting:
      enabled: false
      value: 1.0
      amount: 1
```

Physical currency notes and coins keep the owner name in their item metadata. `/withdraw` sets the owner to the player, and crafted physical currency is rewritten to the crafting player as well.

![Physical coin](docs/assets/PhysicalCoin.gif)

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
### 🔄 **Currency Exchange**
```yaml
exchange-fee-percentage: 2.5

currencies:
  dollars:
    exchange-rates:
      coins: 0.01  # 1 dollar = 0.01 coins
  coins:
    exchange-rates:
      dollars: 100.0  # 1 coin = 100 dollars
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
<div align="center">

![ShopGUI](docs/assets/ShopGUI.png)

</div>

**Core Shop Capabilities:**
- **Creative-style categories (11)** - Default layout follows the creative inventory tab order (operator utilities disabled by default)
- **Favorites system** - Favorite items, browse a dedicated favorites view, and optionally render favorites with a glow highlight (`favorites.yml`)
- **Purchase GUI flow** - Click an item to open a buy menu with quantity +/- controls, confirm/cancel, and back-to-category paging
- **Dynamic pricing** - Buy prices can be calculated from sell prices using a configurable multiplier
- **Category management** - Enable/disable categories, set icons, and control slots with `page:slot`
- **Search + paging** - Search across categories and navigate pages
- **Optional disabled display** - Show items with no buy price as disabled instead of hiding them (`show-unpriced-items`)

**Shop GUI Interface:**
- **Category browser** - Navigate creative-style category tabs
- **Item preview** - See item details and buy prices
- **Balance display** - Live balance display in the GUI
- **Sound effects** - Audio feedback for purchases and navigation (configured in `gui.yml`)
- **Pagination** - Navigate through multiple pages of items
- **Search functionality** - Find items across all categories


### 🏪 **Shop Configuration**
```yaml
# shop.yml
shop:
  enabled: true
  buy-currency: "dollars"
  buy-multiplier: 2.0
  items-per-page: 28
  show-unpriced-items: false

categories:
  building_blocks:
    display-name: "Building Blocks"
    icon: STONE
    enabled: true
    slot: "1:0"
    items:
      - STONE
      - COBBLESTONE
      - BRICKS
      # ... more items
```

**Available Categories (Default Layout):**
- **Building Blocks**
- **Colored Blocks**
- **Natural Blocks**
- **Functional Blocks**
- **Redstone Blocks**
- **Tools & Utilities**
- **Combat**
- **Food & Drinks**
- **Ingredients**
- **Spawn Eggs**
- **Operator Utilities** (disabled by default)

### 🎯 **Shop Commands**
```bash
/shop                    # Open main shop interface
/shop help               # Show shop help
```

---

## 💰 **Sell System**

### 📤 **Sell Features**
The sell system provides multiple ways for players to convert their items into currency, from quick command-based selling to an interactive GUI interface.
<div align="center">

![Relish-Economy-SellGUI.gif](https://cdn.modrinth.com/data/5RyYvL8C/images/a1244aaf472b1276888f99278b0e4da431bf892c.gif)

</div>

**Sell Methods:**
- **Command-based selling** - Quick `/sellhand`, `/sellhotbar`, and `/sellall` commands (Free)
- **Interactive Sell GUI** - Drag-and-drop interface for selective selling (Premium)
- **Auto-grab functionality** - Automatically collect sellable items from inventory
- **Price calculation** - Real-time value calculation with currency conversion
- **Confirmation system** - Prevent accidental sales with confirmation prompts

![SellGUI](docs/assets/SellGUI.png)

**Advanced Sell Features:**
- **Multi-currency payouts** - Receive payment in configured target currency
- **Bulk selling** - Sell entire stacks or inventory contents at once
- **500+ sellable items** - Comprehensive item price database
- **Composter selling** - Throw items on composter for instant selling (Premium)
- **Transaction logging** - Track all sell transactions for auditing
- **Sold-items hover summary** - Hover chat output to view sold item breakdown


<div align="center">

![Sell Hover Preview](docs/assets/hover_items_prices.png)

</div>

### 🎮 **Sell Commands (Free)**
```bash
/sellhand               # Sell the item in your hand
/sellhotbar             # Sell all sellable items in your hotbar
/sellall                # Sell all sellable items in inventory
/sellall confirm        # Confirm bulk selling with safety check
```

These commands work without a premium license. Only the sell GUI, composter selling, and sell block interactions are premium.

### 🖱️ **Sell GUI Interface** ⭐
The premium Sell GUI provides an intuitive drag-and-drop interface for item selling:


**GUI Features:**
- **Drag-and-drop zones** - Simply drag items to sell them
- **Quick grab button** - Auto-collect all sellable items from inventory
- **Live pricing** - See total sale value update as you add items
- **Total calculator** - View total sale value before confirming
- **Confirmation system** - Confirm sale with total summary
- **Sound effects** - Audio feedback for all interactions


### ⚙️ **Sell Configuration**
```yaml
# prices.yml
sell:
  enabled: true

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

### 💰 **Physical Currency**

Players can withdraw supported currencies into physical items, trade them, then deposit them back with `Shift + Right-Click`.

Each currency can control this separately:
- `currencies.<name>.physical-item.withdraw-enabled`
- `currencies.<name>.physical-item.deposit-enabled`
- `currencies.<name>.crafting.enabled`

Crafted physical currency also stores the crafting player as the owner, matching withdrawn notes and coins.




---

## 🎨 **GUI Features** ⭐

### 🛒 **Shop Interface**
The premium shop GUI provides an elegant and user-friendly shopping experience with full customization options.
<div align="center">

![ShopGUI](docs/assets/ShopGUI.png)

</div>

**Interface Highlights:**
- **Category browsing** with configurable icons and colors
- **Item purchasing** with multiple quantity options (1, 32, 64)
- **Balance display** with live updates
- **Sound effects** for all interactions
- **Configurable GUI size** and layout options
- **Permission-based category access**
  

### 💼 **Sell Interface**
The premium sell GUI offers an intuitive drag-and-drop experience for item selling.



**Interface Features:**
- **Drag-and-drop** item selling with visual feedback
- **Quick grab** button to auto-collect sellable items
- **Live value** calculation and display
- **Confirmation system** with total sale summary
- **Sound effects** and particle animations
- **Multi-currency** payout options


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
- Towny bank deposits are supported (including `/t deposit <amount>` flow)

### 📊 **PlaceholderAPI Integration**

**Balance Placeholders:**
```
%relisheconomy_balance_[currency]%        # Raw balance (e.g. 1000.50)
%relisheconomy_balance_[currency]_[type]_[style]%  # Formatting options (e.g. 1,250.00 via full_plain)
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

![PlacholdersAPI](docs/assets/PlacholdersAPI.png)

---

## 🌍 **Multi-Language Support**

### 🗣️ **Built-in Languages**
- 🇺🇸 **English** (en) - Complete
- 🇸🇦 **Arabic** (ar) - Complete
- 🇵🇹 **Portuguese** (pt) - Complete

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
- **Real-time read mode** for external integrations
- **Database health monitoring**

---

## 📄 **License**

**RelishEconomy is proprietary software. All rights reserved.**

### License Types

#### 🆓 Free Version
- Available without license key
- Includes multi-currency, exchange, baltop, migration, and command-based selling
- May be used on unlimited servers
- **NOT open source** - modification and redistribution prohibited

#### ⭐ Premium Version
- Requires valid license key from M5LB
- Includes premium-only features such as Shop GUI, Sell GUI, physical currency, and premium block interactions
- License key tied to purchaser and server count
- **NOT open source** - modification and redistribution prohibited

For full license terms, see [LICENSE](https://github.com/iM5LB/relisheconomy?tab=License-1-ov-file) file.

### Obtain Premium License

To get a premium license key:
- 🛒 **Buy a key from [M5LB Store](https://m5lb.run.place/)**

---
<div align="center">

**Made with ❤️ by M5LB**

</div>
