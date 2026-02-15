# PlaceholderAPI Integration

RelishEconomy provides comprehensive PlaceholderAPI support with caching for optimal performance.

## Installation

1. Install [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/)
2. Install RelishEconomy
3. Placeholders are automatically registered

## Balance Placeholders

### Raw Balance
```
%relisheconomy_balance_[currency]%
```
Returns the raw balance as a number (e.g., `1000.50`)

Also supported:
```
%relisheconomy_balance_formatted%
%relisheconomy_balance_formatted_[currency]%
```
These return the formatted balance variant.

**Examples:**
- `%relisheconomy_balance_dollars%` → `1000.50`
- `%relisheconomy_balance_coins%` → `25`
- `%relisheconomy_balance%` → Uses default currency

### Formatted Balance
```
%relisheconomy_formatted_[currency]%
```
Returns the formatted balance with currency symbol and color (e.g., `$1,000.50`)

Advanced formatted variants are also supported:
```
%relisheconomy_formatted_[currency]_[type]_[style]%
```

`type`:
- `compact` -> `1.2k`, `3.4m`, `2b`
- `full` -> full number with separators
- `raw` -> numeric only (no currency symbol)

`style`:
- `colored` (default)
- `plain`

**Examples:**
- `%relisheconomy_formatted_dollars%` → `$1,000.50`
- `%relisheconomy_formatted_coins%` → `◎25`
- `%relisheconomy_formatted%` → Uses default currency

Additional examples:
- `%relisheconomy_formatted_dollars_compact_colored%` -> compact colored format
- `%relisheconomy_formatted_dollars_compact_plain%` -> compact plain format
- `%relisheconomy_formatted_dollars_full_plain%` -> full plain format
- `%relisheconomy_formatted_dollars_raw_plain%` -> raw numeric plain format

## Leaderboard Placeholders

You can use either:
```
%relisheconomy_baltop_...%
%relisheconomy_leaderboard_...%
%relisheconomy_top_...%
```

### Player Names
```
%relisheconomy_baltop_[position]_[currency]_name%
```
Returns the player name at the specified leaderboard position.

**Examples:**
- `%relisheconomy_baltop_1_dollars_name%` → `Steve`
- `%relisheconomy_baltop_5_coins_name%` → `Alex`

### Formatted Balances
```
%relisheconomy_baltop_[position]_[currency]_balance%
```
Returns the formatted balance at the specified position.

**Examples:**
- `%relisheconomy_baltop_1_dollars_balance%` → `$50,000.00`
- `%relisheconomy_baltop_3_coins_balance%` → `◎1,250`

### Raw Balances
```
%relisheconomy_baltop_[position]_[currency]_raw%
```
Returns the raw balance number at the specified position.

**Examples:**
- `%relisheconomy_baltop_1_dollars_raw%` → `50000.00`
- `%relisheconomy_baltop_10_coins_raw%` → `500`

## Player Rank

### Current Rank
```
%relisheconomy_rank_[currency]%
```
Returns the player's current rank in the leaderboard.

**Examples:**
- `%relisheconomy_rank_dollars%` → `15`
- `%relisheconomy_rank_coins%` → `Unranked`

## Currency Information

### Currency Symbol
```
%relisheconomy_currency_[currency]_symbol%
```
Returns the currency symbol.

**Examples:**
- `%relisheconomy_currency_dollars_symbol%` → `$`
- `%relisheconomy_currency_coins_symbol%` → `◎`

### Display Name
```
%relisheconomy_currency_[currency]_display%
%relisheconomy_currency_[currency]_displayname%
```
Returns the currency display name.

**Examples:**
- `%relisheconomy_currency_dollars_display%` → `Dollars`
- `%relisheconomy_currency_coins_displayname%` → `Coins`

### Starting Balance
```
%relisheconomy_currency_[currency]_starting%
%relisheconomy_currency_[currency]_startingbalance%
```
Returns the starting balance for new players.

**Examples:**
- `%relisheconomy_currency_dollars_starting%` → `100.00`
- `%relisheconomy_currency_coins_startingbalance%` → `50.00`

### Default Currency Check
```
%relisheconomy_currency_[currency]_default%
```
Returns `true` if the currency is the default currency, `false` otherwise.

**Examples:**
- `%relisheconomy_currency_dollars_default%` → `true`
- `%relisheconomy_currency_coins_default%` → `false`

### Currency Name
```
%relisheconomy_currency_[currency]_name%
%relisheconomy_currency%
```
Returns the currency internal name. Without parameters, returns default currency.

**Examples:**
- `%relisheconomy_currency_dollars_name%` → `dollars`
- `%relisheconomy_currency%` → `dollars` (default)

## Utility Placeholders

### Has Enough Money
```
%relisheconomy_hasenough_[amount]_[currency]%
```
Returns `true` if the player has at least the specified amount, `false` otherwise.

**Examples:**
- `%relisheconomy_hasenough_1000_dollars%` → `true`
- `%relisheconomy_hasenough_50_coins%` → `false`

### Exchange Rates (Premium)
```
%relisheconomy_exchangerate_[from]_[to]%
```
Returns the exchange rate between two currencies.

**Examples:**
- `%relisheconomy_exchangerate_dollars_coins%` → `0.0100`
- `%relisheconomy_exchangerate_coins_dollars%` → `100.0000`

## Server Statistics

### Currency Count
```
%relisheconomy_stats_currencies%
```
Returns the total number of configured currencies.

**Example:** `%relisheconomy_stats_currencies%` → `2`

### Cached Accounts
```
%relisheconomy_stats_accounts%
```
Returns the number of accounts currently in cache.

**Example:** `%relisheconomy_stats_accounts%` → `45`

### Database Type
```
%relisheconomy_stats_dbtype%
```
Returns the database type being used.

**Examples:**
- `%relisheconomy_stats_dbtype%` → `sqlite`
- `%relisheconomy_stats_dbtype%` → `mysql`

### Database Health
```
%relisheconomy_stats_dbhealthy%
```
Returns `true` if the database connection is healthy, `false` otherwise.

**Example:** `%relisheconomy_stats_dbhealthy%` → `true`

## Usage Examples

### Scoreboard Example
```yaml
# scoreboard.yml (using a scoreboard plugin)
lines:
  - "&6&lYour Balance"
  - "&f%relisheconomy_formatted_dollars%"
  - "&f%relisheconomy_formatted_coins%"
  - ""
  - "&e&lRank: &f#%relisheconomy_rank_dollars%"
  - ""
  - "&a&lTop Player:"
  - "&f%relisheconomy_baltop_1_dollars_name%"
  - "&f%relisheconomy_baltop_1_dollars_balance%"
```

### Chat Format Example
```yaml
# Chat plugin configuration
format: "&7[&f%relisheconomy_rank_dollars%&7] &f%player_name%&7: %message%"
```

### GUI Example
```yaml
# GUI plugin item
balance-display:
  material: GOLD_INGOT
  name: "&6Your Balance"
  lore:
    - "&fDollars: %relisheconomy_formatted_dollars%"
    - "&fCoins: %relisheconomy_formatted_coins%"
    - ""
    - "&7Rank: #%relisheconomy_rank_dollars%"
```

### Conditional Examples
```yaml
# Using conditional placeholders (with plugins like ConditionalEvents)
conditions:
  - "%relisheconomy_hasenough_1000_dollars% == true"
  - "%relisheconomy_rank_dollars% <= 10"
```

## Performance Notes

- **Caching**: All placeholders are cached for 1 second to improve performance
- **Automatic Cleanup**: Cache is cleaned every minute to prevent memory leaks
- **Player-Specific**: Cache is invalidated when player balances change
- **Error Handling**: Invalid placeholders return empty strings or default values

## Troubleshooting

### Placeholder Not Working
1. Verify PlaceholderAPI is installed and loaded
2. Check that the currency name is correct (case-sensitive)
3. Ensure the target player/account exists in your economy data
4. Use `/papi parse [player] [placeholder]` to test

### Performance Issues
1. Reduce placeholder usage in high-frequency updates
2. Use caching plugins for complex placeholder combinations
3. Monitor server performance with `/papi info`

### Common Mistakes
- Using uppercase currency names (use lowercase)
- Missing currency parameter (defaults to main currency)
- Invalid position numbers in baltop placeholders
- Typos in placeholder names (check spelling)

## Additional Baltop Variants

You can use advanced formatting controls on baltop balances:

```
%relisheconomy_baltop_[position]_[currency]_balance_[type]_[style]%
%relisheconomy_baltop_[position]_[currency]_formatted_[type]_[style]%
```

`type`:
- `compact`
- `full`
- `raw`

`style`:
- `colored` (default)
- `plain`

Examples:
- `%relisheconomy_baltop_1_dollars_balance_compact_plain%`
- `%relisheconomy_baltop_1_dollars_formatted_full_colored%`
- `%relisheconomy_baltop_1_dollars_formatted_raw_plain%`

Extra player identifier placeholder:
```
%relisheconomy_baltop_[position]_[currency]_uuid%
```
