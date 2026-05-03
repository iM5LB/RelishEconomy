# Permissions

Complete reference for all RelishEconomy permissions.

## Permission Structure

RelishEconomy uses a hierarchical permission system:
- `relish.economy.*` - Grants all permissions (admin)
- `relish.economy.<category>` - Grants category permissions
- `relish.economy.<category>.<action>` - Grants specific action

## Default Permissions

These permissions are granted to all players by default:

| Permission | Description | Default |
|------------|-------------|---------|
| `relish.economy.use` | Use the /re command | true |
| `relish.economy.balance` | Check own balance | true |
| `relish.economy.pay` | Transfer money to players | true |
| `relish.economy.baltop` | View leaderboard | true |
| `relish.economy.currency` | View currencies | true |
| `relish.economy.exchange` | Exchange between currencies | true |
| `relish.economy.sell` | Sell items | true |
| `relish.economy.shop` | Buy items from shop | true |
| `relish.economy.withdraw` | Withdraw physical currency | true |

## Admin Permissions

These permissions are for server operators:

| Permission | Description | Default |
|------------|-------------|---------|
| `relish.economy.*` | All permissions | op |
| `relish.economy.admin` | Admin commands | op |
| `relish.economy.balance.others` | Check other players' balances | op |
| `relish.economy.eco` | All eco sub-commands | op |
| `relish.economy.eco.give` | Give money to players | op |
| `relish.economy.eco.take` | Take money from players | op |
| `relish.economy.eco.set` | Set player balances | op |
| `relish.economy.pay.nocooldown` | Bypass pay cooldown | op |

## Command-Specific Permissions

### Balance Command
```
/balance [player] [currency|all]
```

- `relish.economy.balance` - Check own balance
- `relish.economy.balance.others` - Check other players' balances

**Examples**:
```yaml
# LuckPerms
lp group default permission set relish.economy.balance true
lp group moderator permission set relish.economy.balance.others true
```

### Pay Command
```
/pay <player> <amount> [currency]
```

- `relish.economy.pay` - Send money to players
- `relish.economy.pay.nocooldown` - Bypass cooldown

**Examples**:
```yaml
# LuckPerms
lp group vip permission set relish.economy.pay.nocooldown true
```

### Eco Command
```
/eco <give|take|set> <player> <amount> [currency]
```

- `relish.economy.eco` - All eco sub-commands
- `relish.economy.eco.give` - Give money
- `relish.economy.eco.take` - Take money
- `relish.economy.eco.set` - Set balance

**Examples**:
```yaml
# LuckPerms
lp group admin permission set relish.economy.eco true
lp group moderator permission set relish.economy.eco.give true
```

### Currency Command
```
/currency <list|select|info> [name]
```

- `relish.economy.currency` - Manage currencies

**Examples**:
```yaml
# LuckPerms
lp group default permission set relish.economy.currency true
```

### Exchange Command
```
/exchange <from> <to> <amount> [confirm]
```

- `relish.economy.exchange` - Exchange currencies

**Examples**:
```yaml
# LuckPerms
lp group default permission set relish.economy.exchange true
```

### Shop Commands
```
/shop [category]
/sellhand
/sellhotbar
/sellall [confirm]
```

- `relish.economy.shop` - Access shop GUI
- `relish.economy.sell` - Sell items

**Examples**:
```yaml
# LuckPerms
lp group default permission set relish.economy.shop true
lp group default permission set relish.economy.sell true
```

### Withdraw Command
```
/withdraw <currency> <amount>
```

- `relish.economy.withdraw` - Withdraw physical currency

**Examples**:
```yaml
# LuckPerms
lp group vip permission set relish.economy.withdraw true
```

## Currency-Specific Permissions

You can restrict access to specific currencies using permissions:

```yaml
# config.yml
currencies:
  premium_coins:
    name: "premium_coins"
    symbol: "$"
    display-name: "Premium Coins"
    permission: "relish.economy.currency.premium"  # Leave blank ("") to disable requirement
```

**Examples**:
```yaml
# LuckPerms - Grant access to premium currency
lp group vip permission set relish.economy.currency.premium true
```

## Permission Groups Setup

### Default Player Setup
```yaml
# LuckPerms
lp group default permission set relish.economy.use true
lp group default permission set relish.economy.balance true
lp group default permission set relish.economy.pay true
lp group default permission set relish.economy.baltop true
lp group default permission set relish.economy.currency true
lp group default permission set relish.economy.exchange true
lp group default permission set relish.economy.sell true
lp group default permission set relish.economy.shop true
```

### VIP Player Setup
```yaml
# LuckPerms - VIP gets all default + extras
lp group vip parent add default
lp group vip permission set relish.economy.pay.nocooldown true
lp group vip permission set relish.economy.withdraw true
```

### Moderator Setup
```yaml
# LuckPerms - Moderator can check balances and give money
lp group moderator parent add default
lp group moderator permission set relish.economy.balance.others true
lp group moderator permission set relish.economy.eco.give true
```

### Admin Setup
```yaml
# LuckPerms - Admin gets everything
lp group admin permission set relish.economy.* true
```

## Permission Manager Examples

### LuckPerms

**Grant all permissions to admin**:
```
/lp group admin permission set relish.economy.* true
```

**Grant specific permission to player**:
```
/lp user PlayerName permission set relish.economy.balance.others true
```

**Remove permission**:
```
/lp user PlayerName permission unset relish.economy.pay
```

### PermissionsEx (PEX)

**Grant permissions to group**:
```
/pex group admin add relish.economy.*
/pex group moderator add relish.economy.balance.others
```

**Grant permission to player**:
```
/pex user PlayerName add relish.economy.eco.give
```

### GroupManager

**Grant permissions to group**:
```
/mangadd admin relish.economy.*
/mangadd moderator relish.economy.balance.others
```

## Troubleshooting

### Players Can't Use Commands

**Problem**: Players get "You don't have permission" message

**Solution**:
1. Check if permission plugin is installed
2. Verify permissions are set correctly
3. Check for typos in permission nodes
4. Reload permissions: `/lp sync` or `/pex reload`

### Admin Commands Not Working

**Problem**: Admins can't use /eco commands

**Solution**:
1. Verify admin has `relish.economy.eco` permission
2. Check if they're OP: `/op PlayerName`
3. Grant wildcard: `relish.economy.*`

### Currency Access Issues

**Problem**: Players can't use specific currency

**Solution**:
1. Check if currency has permission requirement in config.yml
2. Grant the required permission
3. Reload config: `/re reload`

## Best Practices

### Security
- Don't give `relish.economy.*` to regular players
- Restrict `eco` commands to trusted staff only
- Use currency permissions for premium features
- Regularly audit permission assignments

### Organization
- Use permission groups (default, vip, moderator, admin)
- Inherit permissions using parent groups
- Document custom permission setups
- Test permissions before deploying

### Performance
- Avoid giving unnecessary permissions
- Use wildcards sparingly
- Keep permission hierarchies simple
- Cache permissions when possible

## See Also

- [Commands Reference](Commands.md) - All available commands
- [Configuration Guide](Configuration.md) - Currency permissions setup
- [Quick Start](QuickStart.md) - Getting started guide

