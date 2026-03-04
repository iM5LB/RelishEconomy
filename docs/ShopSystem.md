# Shop System

Complete guide to the interactive shop system (Premium Feature).

## Overview

The Shop System allows players to buy items through an intuitive GUI interface. Items are organized into categories for easy browsing.

> **Premium Feature**: The Shop System requires a premium license purchased from the [M5LB Store](https://m5lb.run.place/). Premium source code is not shared - the license key activates these features.

## Accessing the Shop

### Method 1: Command
```
/shop
/shop <category>
```

### Method 2: Block Interaction
Right-click the configured shop block (default: Emerald Block):

```yaml
# config.yml
shop-gui-block: EMERALD_BLOCK
```

Shop access can be toggled in `shop.yml`:

```yaml
shop:
  enabled: true
```

## Shop Categories

The shop is organized into categories for easy navigation:

### Default Categories

| Category | Icon | Description |
|----------|------|-------------|
| **Wood** | Oak Log | All wood types, planks, stairs, slabs |
| **Stone** | Stone | Stone variants, andesite, granite, diorite |
| **Deepslate** | Deepslate Bricks | Deepslate family and tuff blocks |
| **Bricks** | Bricks | All brick types and variants |
| **Sand & Sandstone** | Sandstone | Sand and sandstone variants |
| **Color Blocks** | White Wool | Wool, concrete, terracotta, carpet |
| **Natural Blocks** | Grass Block | Dirt, grass, plants, flowers |
| **Glass** | Glass | Glass blocks and panes |
| **Lighting** | Glowstone | Light sources and candles |
| **Decorations** | Painting | Decorative items and furniture |

### Enabling/Disabling Categories

Edit `shop.yml` to control which categories are available:

```yaml
categories:
  wood:
    enabled: true  # Category is available
    
  mining_ores:
    enabled: false  # Category is hidden
```

## Configuring Prices

### Setting Sell Prices

Edit `prices.yml` to set how much players receive when selling:

```yaml
prices:
  DIAMOND: 100.0
  EMERALD: 50.0
  GOLD_INGOT: 25.0
  IRON_INGOT: 10.0
```

### Buy Price Calculation

Buy prices are automatically calculated using a multiplier:

```yaml
# shop.yml
shop:
  buy-multiplier: 2.0  # Buy price = Sell price × 2.0
```

**Example**:
- Sell price: $10
- Buy multiplier: 2.0
- Buy price: $20

### Per-Item Currency

You can set different currencies for specific items:

```yaml
# prices.yml
prices:
  DIAMOND: { price: 100, currency: "dollars" }
  EMERALD: { price: 50, currency: "coins" }
```

Sell system availability is controlled in `prices.yml`:

```yaml
sell:
  enabled: true
```

## Using the Shop

### Buying Items

1. Open the shop with `/shop` or right-click shop block
2. Click a category to browse items
3. Click an item to purchase:
   - **Left Click**: Buy 1 item
   - **Middle Click**: Buy 32 items (half stack)
   - **Right Click**: Buy 64 items (full stack)

### Navigation

- **Back Button**: Return to category selection
- **Previous Page**: Go to previous page of items
- **Next Page**: Go to next page of items
- **Balance Display**: Shows your current balance
- **Close Button**: Exit the shop

## Customizing the Shop GUI

### GUI Layout

Edit `gui.yml` to customize the shop interface:

```yaml
shop-gui:
  title: "<#fdb833><bold>Shop GUI"
  size: 54  # Inventory size (9, 18, 27, 36, 45, 54)
  items-per-page: 28
```

### Button Positions

Customize where buttons appear:

```yaml
shop-gui:
  buttons:
    back:
      slot: 45
      material: ARROW
      name: "<yellow><bold>← Back to Categories"
    
    balance:
      slot: 49
      material: GOLD_INGOT
      name: "<#fdb833><bold>Your Balance"
    
    close:
      slot: 53
      material: BARRIER
      name: "<red><bold>Close Shop"
```

### Glass Pane Decoration

Add decorative glass panes:

```yaml
shop-gui:
  glass-panes:
    enabled: true
    material: GRAY_STAINED_GLASS_PANE
    name: " "  # Empty name
```

### Item Display Format

Customize how items are displayed:

```yaml
shop-gui:
  shop-item:
    name: "<#fdc43f><bold>{item_name}"
    lore:
      - ""
      - "<dark_gray>▸ <gray>Buy Price: {buy_price}"
      - "<dark_gray>▸ <gray>Sell Price: {sell_price}"
      - ""
      - "<dark_gray>▸ <#ffe246>Left Click: <white>Buy 1"
      - "<dark_gray>▸ <#ffe246>Middle Click: <white>Buy 32"
      - "<dark_gray>▸ <#ffe246>Right Click: <white>Buy 64"
```

## Adding Custom Categories

### Step 1: Define Category

Add to `shop.yml`:

```yaml
categories:
  custom_category:
    display-name: "Custom Items"
    icon: DIAMOND
    description: "Special custom items"
    enabled: true
    slot: "2:0"  # Row 2, Column 0
    items:
      - DIAMOND
      - EMERALD
      - NETHERITE_INGOT
```

### Step 2: Set Prices

Add prices in `prices.yml`:

```yaml
prices:
  DIAMOND: 100.0
  EMERALD: 50.0
  NETHERITE_INGOT: 1000.0
```

### Step 3: Reload

```
/re reload
```

## Managing Shop Items

### Adding Items to Category

Edit the category's `items:` list in `shop.yml`:

```yaml
categories:
  wood:
    items:
      - OAK_LOG
      - SPRUCE_LOG
      - BIRCH_LOG
      - NEW_WOOD_TYPE  # Add new item
```

### Removing Items

Simply delete the item from the list:

```yaml
categories:
  wood:
    items:
      - OAK_LOG
      - SPRUCE_LOG
      # BIRCH_LOG removed
```

### Making Items Unsellable

Set price to -1 or remove from prices.yml:

```yaml
prices:
  SPAWNER: -1  # Cannot be sold
```

## Sound Effects

Customize shop sounds in `gui.yml`:

```yaml
sounds:
  gui:
    open: BLOCK_CHEST_OPEN
    close: BLOCK_CHEST_CLOSE
    click: UI_BUTTON_CLICK
    error: ENTITY_VILLAGER_NO
  
  transaction:
    purchase: ENTITY_PLAYER_LEVELUP
  
  volume: 1.0
  pitch: 1.0
```

## Permissions

| Permission | Description |
|------------|-------------|
| `relish.economy.shop` | Access the shop |
| `relish.economy.shop.category.<name>` | Access specific category |

**Example**:
```yaml
# LuckPerms - Restrict premium category
lp group vip permission set relish.economy.shop.category.premium true
```

## Troubleshooting

### Shop Not Opening

**Problem**: Right-clicking block doesn't open shop

**Solutions**:
1. Verify license key is valid
2. Check `shop-gui-block` in config.yml
3. Ensure player has `relish.economy.shop` permission
4. Check console for errors

### Items Not Showing

**Problem**: Category is empty or items missing

**Solutions**:
1. Verify items are listed in `shop.yml`
2. Check if items have prices in `prices.yml`
3. Ensure category is enabled
4. Reload config: `/re reload`

### Wrong Prices

**Problem**: Buy/sell prices are incorrect

**Solutions**:
1. Check `prices.yml` for sell prices
2. Verify `buy-multiplier` in `shop.yml`
3. Clear cache: `/re reload`
4. Check for per-item currency settings

### Permission Issues

**Problem**: Players can't access shop

**Solutions**:
1. Grant `relish.economy.shop` permission
2. Check category-specific permissions
3. Verify permission plugin is working
4. Test with OP player

## Best Practices

### Pricing Strategy
- Set reasonable buy/sell ratios (2.0-3.0 multiplier)
- Balance economy with server progression
- Adjust prices based on item rarity
- Monitor inflation/deflation

### Category Organization
- Group similar items together
- Use clear, descriptive names
- Limit items per category (20-50)
- Disable unused categories

### Performance
- Don't add too many items (500+ total)
- Use appropriate GUI size
- Optimize glass pane usage
- Regular database maintenance

## See Also

- [Sell System](SellSystem.md) - Selling items guide
- [Configuration Guide](Configuration.md) - Full config reference
- [Commands Reference](Commands.md) - All commands
