# Configuration Guide

## Main Configuration (config.yml)

### Basic Settings

```yaml
# Configuration version (DO NOT EDIT)
config-version: 2

# License key for premium features
license-key: ""

# Debug mode for troubleshooting
debug-mode: false

# Automatic update checking
check-for-updates: true

# bStats metrics (Plugin ID is hardcoded)
metrics:
  enabled: true

# Language (en, ar, pt, or custom)
language: en
```

### Database Configuration

#### SQLite (Default)
```yaml
database:
  type: sqlite
  real-time-read: false
```

#### MySQL (For Networks)
```yaml
database:
  type: mysql
  real-time-read: false
  
  mysql:
    host: localhost
    port: 3306
    database: relisheconomy
    username: root
    password: your_password
```

Balances store player identity and economy values using:
- `uuid`
- `player_name`
- `discord_id`
- `currency`
- `balance`
- `last_modified`

### Currency Configuration

Define unlimited currencies with custom properties:

```yaml
currencies:
  dollars:
    symbol: "$"                    # Currency symbol (1-3 characters)
    display-name: "Dollars"        # User-friendly name
    color: "<green>"              # MiniMessage color format
    default: true                 # One currency must be default
    starting-balance: 100.0       # New player starting amount
    payments-enabled: true        # Allow /pay command
    permission: null              # Optional permission requirement
    decimals-enabled: true        # Show decimal places
    
  coins:
    symbol: "◎"
    display-name: "Coins"
    color: "<gold>"
    default: false
    starting-balance: 50.0
    payments-enabled: true
    permission: "relish.economy.coins"  # Require permission
    decimals-enabled: false       # Whole numbers only
```

### Exchange Rates (Premium)

Configure currency conversion rates:

```yaml
exchange-rates:
  dollars:
    coins: 0.01    # 1 dollar = 0.01 coins
  coins:
    dollars: 100   # 1 coin = 100 dollars
```

### Performance Settings

```yaml
# Baltop cache duration (seconds)
baltop-cache-duration: 300

# Pay command cooldown (seconds)
pay-cooldown: 3

# Maximum balance to prevent overflow
max-balance: 1000000000000

# Minimum transaction amount
min-transaction: 0.01
```

### Premium Features Configuration

```yaml
# Composter selling feature
composter-selling:
  enabled: true
  cooldown: 1000  # Milliseconds between sells

# GUI block interactions
sell-gui-block: COMPOSTER
shop-gui-block: CHEST

# Exchange fee percentage
exchange-fee: 2.5
```

## Language Files

### English (lang/en.yml)
```yaml
balance:
  current: "<green>Your balance: {balance}"
  other: "<green>{player}'s balance: {balance}"
  
pay:
  sent: "<green>Sent {amount} to {player}"
  received: "<green>Received {amount} from {player}"
  
errors:
  insufficient_funds: "<red>Insufficient funds!"
  player_not_found: "<red>Player not found!"
```

### Arabic (lang/ar.yml)
```yaml
balance:
  current: "<green>رصيدك: {balance}"
  other: "<green>رصيد {player}: {balance}"
  
pay:
  sent: "<green>تم إرسال {amount} إلى {player}"
  received: "<green>تم استلام {amount} من {player}"
```

### Portuguese (lang/pt.yml)
```yaml
balance:
  current: "<green>Seu saldo: {balance}"
  other: "<green>Saldo de {player}: {balance}"
  
pay:
  sent: "<green>Enviado {amount} para {player}"
  received: "<green>Recebido {amount} de {player}"
```

### Custom Languages
Create `lang/[code].yml` for any language:
- Copy `en.yml` as template
- Translate all messages
- Set `language: [code]` in config.yml

## Premium Configuration Files

### Item Prices (prices.yml)
```yaml
# Sell system toggle
sell:
  enabled: true

# Target currency for selling
target-currency: dollars

# Item prices
prices:
  DIAMOND: 100.0
  GOLD_INGOT: 50.0
  IRON_INGOT: 10.0
  STONE: 0.1

# Per-item currencies (optional)
# Use object format under prices:
# EMERALD: { price: 150, currency: "coins" }
```

### Shop Configuration (shop.yml)
```yaml
# Shop settings
shop:
  enabled: true
  buy-multiplier: 1.5  # 50% markup from sell price

# Available categories
categories:
  blocks:
    icon: STONE
    enabled: true
  tools:
    icon: DIAMOND_PICKAXE
    enabled: true
    
# Available items per category
items:
  blocks:
    - STONE
    - COBBLESTONE
    - DIRT
  tools:
    - WOODEN_PICKAXE
    - STONE_PICKAXE
```

### GUI Customization (gui.yml)
```yaml
shop:
  title: "<gold>Shop"
  size: 54  # Inventory size (9, 18, 27, 36, 45, 54)
  items-per-page: 28
  
  # Glass pane decoration
  glass-panes:
    enabled: true
    material: GRAY_STAINED_GLASS_PANE
    
  # Button positions
  buttons:
    previous: 45
    next: 53
    balance: 49
    
sell:
  title: "<red>Sell Items"
  size: 54
  
  buttons:
    shop: 45
    grab: 49
    confirm: 53
    
# Sound effects
sounds:
  gui:
    open: BLOCK_CHEST_OPEN
    close: BLOCK_CHEST_CLOSE
    click: UI_BUTTON_CLICK
  volume: 1.0
  pitch: 1.0
```

## Database Schema Customization

For advanced users, you can customize table and column names:

```yaml
database:
  schema:
    balances:
      table: "player_balances"
      columns:
        uuid: "player_uuid"
        player_name: "player_name"
        discord_id: "discord_id"
        currency: "currency_name"
        balance: "amount"
        
    transactions:
      table: "economy_transactions"
      columns:
        id: "transaction_id"
        uuid: "player_uuid"
        amount: "transaction_amount"
```

## Configuration Validation

RelishEconomy automatically validates and fixes configuration issues:

- Invalid values are reset to defaults
- Missing sections are added
- Deprecated options are removed
- Missing keys are merged for `config.yml`, `lang/*.yml`, `shop.yml`, `prices.yml`, and `gui.yml`
- Original files are backed up before updates using names like `config-backup-YYYYMMDD-HHMMSS.yml`
- Validation report is logged on startup

Use `/re reload` to reload configuration without restarting the server.

## Best Practices

### Currency Design
- Use short, memorable symbols (1-3 characters)
- Choose distinct colors for each currency
- Set reasonable starting balances
- Consider decimal vs whole number currencies

### Performance
- Use SQLite for small servers (< 500 players)
- Use MySQL for large networks (500+ players)
- Enable real-time read only if you manually update balances in the DB (Discord/Web integration)
- Adjust cache durations based on server size

### Security
- Restrict admin permissions appropriately
- Set reasonable maximum balances
- Use minimum transaction amounts to prevent spam
- Regular database backups recommended
