<div align="center">

## ðŸ’° Multi-Currency Economy â€¢ Shop â€¢ Sell GUI â€¢ Physical Currency

![Relish-Economy-Logo](https://cdn.modrinth.com/data/cached_images/9df4655d0afd67ba097405f931695951fcb513f2_0.webp)
[![M5LB Store Banner](https://github.com/iM5LB/RelishEconomy/raw/main/docs/assets/M5LBStore.png)](https://m5lb.run.place/)
[![Discord](https://img.shields.io/badge/Discord-Support-7289da?style=for-the-badge&logo=discord)](https://discord.gg/hjKcHavRjT)
[![Documentation](https://img.shields.io/badge/Docs-Read-blue?style=for-the-badge&logo=gitbook)](https://im5lb.github.io/relisheconomy)
[![Issues](https://img.shields.io/badge/ðŸ›%20Issues-Report-orange?style=for-the-badge)](https://github.com/iM5LB/relisheconomy/issues)
[![Store](https://img.shields.io/badge/Store-License%20Keys-gold?style=for-the-badge)](https://m5lb.run.place/)
[![Donate](https://img.shields.io/badge/ðŸ’–%20Donate-Love-ff69b4?style=for-the-badge)](https://creators.sa/m5lb)

</div>

---

## ðŸŒŸ **Why Choose RelishEconomy?**

RelishEconomy provides a solid economy foundation with multi-currency support, database flexibility, and seamless plugin integrations. Built for modern Minecraft servers with performance and reliability in mind.

### âœ¨ **Key Highlights**

ðŸ¦ **Multi-Currency System** - Support for multiple custom currencies  
ðŸš€ **High Performance** - Advanced caching with Caffeine for fast operations  
ðŸ”§ **Full Integration** - Vault and PlaceholderAPI support  
ðŸ—„ï¸ **Database Flexibility** - SQLite and MySQL support  
ðŸŒ **Multi-Language** - Built-in English, Arabic, Portuguese, and Polish translations  

---

## ðŸ“‹ **Requirements**

| Component | Requirement |
|-----------|-------------|
| **Minecraft** | 1.21+ |
| **Server** | Paper, Purpur, or Paper-based forks |
| **Java** | 21+ |
| **Soft Dependencies** | Vault (recommended), PlaceholderAPI (optional) |

---

## ðŸš€ **Features Overview**

### ðŸ†“ **Free Version**
- âœ… Basic economy commands (`/balance`, `/pay`, `/baltop`, `/eco`)
- âœ… **Multi-currency system** with custom properties
- âœ… Per-currency formatting, permissions, and decimal control
- âœ… **Currency exchange** with per-currency exchange rates
- âœ… Command-based selling (`/sellhand`, `/sellhotbar`, `/sellall`)
- âœ… Sold-item hover breakdowns for sell commands
- âœ… Baltop leaderboard placeholders and balance placeholders
- âœ… Data migration from other plugins
- âœ… Player username storage alongside UUID balances
- âœ… Towny and Vault economy compatibility
- âœ… Vault and PlaceholderAPI support
- âœ… SQLite and MySQL support
- âœ… Config validation, backup, and auto-recovery for bundled files

### â­ **Premium Version**
- â­ **Shop GUI** with category browsing
- â­ **Sell GUI** for item selling
- â­ **Transaction Logs GUI** for sell history navigation
- â­ **Block interactions** (shop/sell blocks)
- â­ **GUI customization** and interactions
- â­ **Physical currency withdraw and shift-deposit**
- â­ **ATM GUI** for physical currency deposit and withdraw
- â­ **Craftable physical currency with owner metadata**
- â­ **Custom model data** support for physical currencies
- â­ **Natural-source currency conversion** for configured item sources
- â­ **Composter selling** - throw items on composter to sell them



---

## ðŸ“¦ **Installation**

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

## ðŸŽ® **Commands & Usage**

### ðŸ‘¤ **Player Commands**

| Command | Description | Example |
|---------|-------------|---------|
| `/balance [player] [currency]` | Check balance | `/bal coins` |
| `/pay <player> <amount>` | Send money | `/pay Steve 100` |
| `/baltop [currency] [page]` | View leaderboard | `/baltop dollars 2` |
| `/currency <list\|info>` | View currencies | `/currency list` |
| `/exchange <from> <to> <amount>` | Convert currencies | `/exchange dollars coins 500` |
| `/shop` â­ | Open shop GUI | `/shop` |
| `/shop help` â­ | Show shop help | `/shop help` |
| `/sell [subcommands]` â­ | Open sell GUI | `/sell price` |
| `/re atm` â­ | Open ATM GUI | `/re atm` |
| `/sellhand` | Sell item in hand | `/sellhand` |
| `/sellhotbar` | Sell hotbar items | `/sellhotbar` |
| `/sellall` | Sell all items | `/sellall confirm` |
| `/withdraw <currency> <amount>` â­ | Get physical currency | `/withdraw coins 10` |

### ðŸ‘‘ **Admin Commands**

| Command | Description | Example |
|---------|-------------|---------|
| `/eco <give\|take\|set> <player> <amount>` | Manage balances | `/eco give Steve 1000` |
| `/re reload` | Reload configuration | `/re reload` |
| `/re migrate <plugin> <currency>` | Import from other plugins | `/re migrate essentials dollars` |

### ðŸ’¡ **Amount Shortcuts**
- `k` = thousand (e.g., `5k` = 5,000)
- `m` = million (e.g., `2m` = 2,000,000)  
- `b` = billion (e.g., `1b` = 1,000,000,000)

---

## ðŸ”§ **Configuration**

### **Currency Setup**
```yaml
currencies:
  dollars:
    enabled: true
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
      value-per-item: 1.0
      deposit-enabled: true
      atm-deposit: true
      deposit-action:
        enabled: true
        require-sneak: true
        click: RIGHT
      withdraw-enabled: true
      owner-enabled: true
      name: "<green><bold>Dollar Bill"
      lore:
        - "<gray>Value: {formatted_amount}"
        - "<gray>Owner: <white>{owner}"
      custom-model-data: -1

  coins:
    enabled: true
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
      value-per-item: 1.0
      deposit-enabled: true
      atm-deposit: true
      deposit-action:
        enabled: true
        require-sneak: true
        click: RIGHT
      withdraw-enabled: true
      owner-enabled: true
      name: "<gold><bold>Gold Coin"
      lore:
        - "<gray>Value: {formatted_amount}"
        - "<gray>Owner: <white>{owner}"
      custom-model-data: -1
      natural-source:
        enabled: true
        match-any-meta: false
        materials:
          - GOLD_NUGGET: 1
          - GOLD_INGOT: 9
          - GOLD_BLOCK: 81
```

### ðŸ—„ï¸ **Database Options**
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

â­ Physical currency notes and coins keep the owner name in their item metadata. `/withdraw` sets the owner to the player, crafted physical currency is rewritten to the crafting player, and custom model data can be applied per currency item.

![Physical coin](https://github.com/iM5LB/RelishEconomy/raw/main/docs/assets/PhysicalCoin.gif)

â­ Natural-source currency conversion can also turn configured gameplay item sources into the physical currency item itself. This is configured per currency.

![Natural-currency](https://github.com/iM5LB/RelishEconomy/raw/main/docs/assets/Natural-currency.gif)


â­ ATM menu for physical currencies. Players can deposit supported currency items into the ATM deposit slots, switch between currencies, choose withdraw amounts, and confirm the action from a single GUI.

**ATM Highlights:**
- **Deposit tray** - Queue supported physical currency items for deposit
- **Withdraw flow** - Select currency, adjust amount, and withdraw as physical items
- **Block access** - Open the ATM from a configured block interaction
- **Shop-style layout** - Uses the same focused quantity workflow as the purchase GUI

**ATM Config**
```yaml
atm:
  enabled: true
  block:
    material: LOOM
    require-sneak: true
```

![ATM Overview](https://github.com/iM5LB/RelishEconomy/raw/main/docs/assets/ATM-Overview.gif)

### ðŸ”„ **Currency Exchange**
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

### ðŸ”„ **Data Migration**

RelishEconomy can import data from other economy plugins:

**Supported Plugins:**
- **EssentialsX** - Import from userdata files
- **CMI** - Import from SQLite database
- **TokenManager** - Import token balances
- **PlayerPoints** - Import point balances
- **CoinsAPI** - Import coin balances
- **GemsEconomy** - Import gem balances


**Migration Features:**
- âœ… **Automatic detection** of source plugin data
- âœ… **UUID conversion** for modern Minecraft
- âœ… **Offline player support** - migrates all accounts
- âœ… **Progress tracking** with detailed reports
- âœ… **Async processing** - no server lag

---

## â­ **Shop System**

### ðŸ“¦ **Shop Features**
RelishEconomy's premium shop system provides a comprehensive item marketplace with intuitive GUI interfaces and flexible configuration options.
<div align="center">

![ShopGUI](https://github.com/iM5LB/RelishEconomy/raw/main/docs/assets/ShopGUI.png)

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


### ðŸª **Shop Configuration**
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

### ðŸŽ¯ **Shop Commands**
```bash
/shop                    # Open main shop interface
/shop help               # Show shop help
```

---

## ðŸ’° **Sell System**

### ðŸ“¤ **Sell Features**
The sell system provides multiple ways for players to convert their items into currency, from quick command-based selling to an interactive GUI interface.
<div align="center">

![Relish-Economy-SellGUI.gif](https://camo.githubusercontent.com/8efd27377280eb89adba7bf94ea798fe5bc5f3cdf40569d2b679be650b299b5d/68747470733a2f2f63646e2e6d6f6472696e74682e636f6d2f646174612f35527959764c38432f696d616765732f613132343461616634373262313237363838386639393237386230653464613433316266383932632e676966)

</div>

**Sell Methods:**
- **Command-based selling** - Quick `/sellhand`, `/sellhotbar`, and `/sellall` commands (Free)
- â­ **Interactive Sell GUI** - Drag-and-drop interface for selective selling
- **Auto-grab functionality** - Automatically collect sellable items from inventory
- **Price calculation** - Real-time value calculation with currency conversion
- **Confirmation system** - Prevent accidental sales with confirmation prompts
- â­ **Logs view** - Open sell history from the sell GUI

![SellGUI](https://github.com/iM5LB/RelishEconomy/raw/main/docs/assets/SellGUI.png)

**Advanced Sell Features:**
- **Multi-currency payouts** - Receive payment in configured target currency
- **Bulk selling** - Sell entire stacks or inventory contents at once
- **500+ sellable items** - Comprehensive item price database
- â­ **Composter selling** - Throw items on composter for instant selling
- **Transaction logging** - Track all sell transactions for auditing
- **Sold-items hover summary** - Hover chat output to view sold item breakdown


<div align="center">

![Sell Hover Preview](https://github.com/iM5LB/RelishEconomy/raw/main/docs/assets/hover_items_prices.png)

</div>

### ðŸŽ® **Sell Commands (Free)**
```bash
/sellhand               # Sell the item in your hand
/sellhotbar             # Sell all sellable items in your hotbar
/sellall                # Sell all sellable items in inventory
/sellall confirm        # Confirm bulk selling with safety check
```

These commands work without a premium license. Only the sell GUI, composter selling, and sell block interactions are premium.

### â­ **Sell GUI Interface**
The premium Sell GUI provides an intuitive drag-and-drop interface for item selling:


**GUI Features:**
- **Drag-and-drop zones** - Simply drag items to sell them
- **Quick grab button** - Auto-collect all sellable items from inventory
- **Live pricing** - See total sale value update as you add items
- **Total calculator** - View total sale value before confirming
- **Confirmation system** - Confirm sale with total summary
- **Sound effects** - Audio feedback for all interactions


### âš™ï¸ **Sell Configuration**
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

### â­ **Sell Block Interactions**
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

### â­ **Physical Currency**

Players can withdraw supported currencies into physical items, trade them, then deposit them back with `Shift + Right-Click`.

Each currency can control this separately:
- `currencies.<name>.physical-item.withdraw-enabled`
- `currencies.<name>.physical-item.deposit-enabled`
- `currencies.<name>.crafting.enabled`
- `currencies.<name>.physical-item.custom-model-data`
- `currencies.<name>.physical-item.natural-source.enabled`

Crafted physical currency also stores the crafting player as the owner, matching withdrawn notes and coins.




---

## â­ **GUI Features**

### â­ **Shop Interface**
The premium shop GUI provides an elegant and user-friendly shopping experience with full customization options.
<div align="center">

![ShopGUI](https://github.com/iM5LB/RelishEconomy/raw/main/docs/assets/ShopGUI.png)

</div>

**Interface Highlights:**
- **Category browsing** with configurable icons and colors
- **Item purchasing** with multiple quantity options (1, 32, 64)
- **Balance display** with live updates
- **Sound effects** for all interactions
- **Configurable GUI size** and layout options
- **Permission-based category access**
  

### â­ **Sell Interface**
The premium sell GUI offers an intuitive drag-and-drop experience for item selling.



**Interface Features:**
- **Drag-and-drop** item selling with visual feedback
- **Quick grab** button to auto-collect sellable items
- **Live value** calculation and display
- **Confirmation system** with total sale summary
- **Sound effects** and particle animations
- **Multi-currency** payout options


### â­ **GUI Customization**
Premium users have full control over GUI appearance and behavior:

**Customization Options:**
- **GUI sizes** - Choose from 9, 18, 27, 36, 45, or 54 slot layouts
- **Custom titles** - Set personalized GUI titles with color codes
- **Item icons** - Use any material as category or button icons
- **Sound effects** - Configure custom sounds for different actions
- **Layout templates** - Pre-designed layouts or create your own
---

## ðŸ”Œ **Integrations**

### ðŸ›ï¸ **Vault API**
Full economy provider implementation:
- `getBalance()`, `depositPlayer()`, `withdrawPlayer()`
- Compatible with **any plugin** using Vault
- Multi-currency support through Vault
- Towny bank deposits are supported (including `/t deposit <amount>` flow)

### ðŸ“Š **PlaceholderAPI Integration**

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

![PlacholdersAPI](https://github.com/iM5LB/RelishEconomy/raw/main/docs/assets/PlacholdersAPI.png)

---

## ðŸŒ **Multi-Language Support**

### ðŸ—£ï¸ **Built-in Languages**
- ðŸ‡ºðŸ‡¸ **English** (en) - Complete
- ðŸ‡¸ðŸ‡¦ **Arabic** (ar) - Complete
- ðŸ‡µðŸ‡¹ **Portuguese** (pt) - Complete
- 🇵🇱 **Polish** (pl) - Complete

### ðŸŒ **Custom Languages**
Create `lang/[code].yml` files for any language:
```yaml
# Example: lang/es.yml for Spanish
balance:
  current: "<green>Tu saldo: {balance}"
  other: "<green>Saldo de {player}: {balance}"
```

---

## ðŸ“ˆ **Performance & Scalability**

### âš¡ **Optimization Features**
- **Caffeine caching** for instant data access
- **Connection pooling** with HikariCP (MySQL)
- **Async operations** for database queries
- **Baltop caching** with configurable duration
- **Auto-cleanup** of stale cache data

### ðŸ“Š **Scalability Options**
- **SQLite** for small-medium servers (0-500 players)
- **MySQL** for large networks (500+ players)
- **Real-time read mode** for external integrations
- **Database health monitoring**

---

## ðŸ“„ **License**

**RelishEconomy is proprietary software. All rights reserved.**

### License Types

#### ðŸ†“ Free Version
- Available without license key
- Includes multi-currency, exchange, baltop, migration, and command-based selling
- May be used on unlimited servers
- **NOT open source** - modification and redistribution prohibited

#### â­ Premium Version
- Requires valid license key from M5LB
- Includes premium-only features such as Shop GUI, Sell GUI, ATM GUI, transaction logs GUI, physical currency, and premium block interactions
- License key tied to purchaser and server count
- **NOT open source** - modification and redistribution prohibited

For full license terms, see [LICENSE](https://github.com/iM5LB/relisheconomy?tab=License-1-ov-file) file.

### Obtain Premium License

To get a premium license key:
- ðŸ›’ **Buy a key from [M5LB Store](https://m5lb.run.place/)**

---
<div align="center">

**Made with â¤ï¸ by M5LB**

</div>
