# RelishEconomy Changelog

## Version 1.0.3-Beta (February 10, 2026)

### 🔧 **Bug Fixes**
- **New Player Balance** - Fixed issue where new players had their balance set instead of added to
  - Starting balance is now added to existing balance instead of overwriting it
  - Prevents accidental balance resets for returning players
  - Maintains proper balance accumulation across sessions

### 🚀 **Upcoming Features**
- **Player-to-Player Trading** - Direct trade system between players
  - Secure trade interface with confirmation system
  - Trade history and logging
  - Configurable trade limits and cooldowns
  
- **Auction House System** - Server-wide marketplace for buying and selling items
  - List items for auction with custom prices
  - Bid on items from other players
  - Automatic payment and item delivery
  - Auction expiration and refund system
  - Search and filter functionality
  - Multi-currency support

---

## Version 1.0.2-Beta (January 23, 2026)

### 🛒 **Multi-Currency Shop Support**

This update adds full multi-currency support to the shop system, making it consistent with the sell functionality.

### ✨ **New Features**
- **Per-Item Shop Currencies** - Shop now uses the same currency system as selling
- **Dynamic Currency Display** - Each item shows its price with the correct currency symbol
- **Consistent Currency Logic** - Shop and sell systems now work identically
- **Automatic Currency Detection** - Items automatically use their configured currency from `prices.yml`

### 🔧 **Technical Changes**
- **ShopManager.java** - `getBuyCurrency(Material)` now returns per-item currencies
- **ShopGUI.java** - Updated to display and handle multiple currencies per item
- **ShopGUIListener.java** - Purchase transactions now use item-specific currencies
- **Balance Display** - Shows default currency balance (since multiple currencies can't be shown at once)

### 📝 **Configuration Updates**
- **shop.yml** - `buy-currency` setting is now deprecated (marked with comments)
- **Documentation** - Updated to reflect new multi-currency shop behavior
- **README.md** - Added deprecation notice for old shop currency setting

### 🎯 **How It Works**
```yaml
# In prices.yml
prices:
  STONE: 0.5                    # Uses default currency (dollars) - shop shows $1.00
  DIAMOND: 
    price: 100
    currency: "coins"           # Shop shows ◎200 (with 2.0x multiplier)
  EMERALD:
    price: 150  
    currency: "gems"            # Shop shows with gems symbol
```

### 🔄 **Backward Compatibility**
- Existing configurations continue to work
- Single-currency setups remain unchanged
- No breaking changes to existing functionality

### 📋 **Migration Notes**
- The `buy-currency` setting in `shop.yml` is now ignored
- Shop items automatically use their currency from `prices.yml`
- No manual configuration changes required

---

## Version 1.0.1-Beta (January 22, 2026)

### 🔄 **Major Feature Redistribution**

This update significantly restructures the premium/free feature distribution to provide more value in the free version while maintaining premium exclusivity for GUI and advanced features.

### ✨ **New Free Features**
- **Multi-Currency System** - Now available in free version with full support for custom currencies
- **Currency Exchange** - Exchange between different currencies with configurable rates
- **Advanced Sell Commands** - `/sellhand` and `/sellall` commands now free for all users
- **Advanced Transaction Logging** - Comprehensive transaction tracking and logging system

### ⭐ **Premium-Only Features**
- **Shop GUI** - Interactive shop interface with category browsing
- **Sell GUI** - Drag-and-drop item selling interface  
- **Block Interactions** - Shop and sell block functionality
- **GUI Customization** - All GUI-related interactions and customizations
- **Physical Currency** - Withdraw currencies as physical items

### 🐛 **Bug Fixes**
- Fixed missing message keys for `/shop help` command
- Added comprehensive help messages for shop commands in both English and Arabic

### 🔧 **Technical Improvements**
- Updated license manager to properly handle new feature distribution
- Removed license checks from exchange and sell commands
- Added license validation for GUI and block interactions
- Improved debugging functionality and error handling

### 📝 **Configuration Updates**
- Updated language files with new shop help messages
- Enhanced message keys for better user experience
- Improved error messages and user feedback

### 🌍 **Localization**
- Added missing Arabic translations for shop help system
- Enhanced English help messages with detailed command information
- Improved RTL support for Arabic language users

---

## Previous Versions

### Version 0.9.0-Alpha
- Initial multi-currency implementation
- Basic shop and sell GUI functionality
- Database migration system
- PlaceholderAPI integration

### Version 0.7.0-Alpha
- Vault integration
- SQLite and MySQL support
- Basic economy commands
- Multi-language support

---

## Migration Guide

### For Server Owners
If you're updating from a previous version:

1. **Backup your data** - Always backup your database and configuration files
2. **Update configuration** - New features may require configuration updates
3. **Check permissions** - Some commands have changed permission requirements
4. **Test features** - Verify that free features work without license restrictions

### For Developers
If you're integrating with RelishEconomy:

1. **API Changes** - Multi-currency is now available in free version
2. **License Checks** - GUI features now require premium license
3. **Command Changes** - Exchange and sell commands are now free

---

## Support

For questions about this update or issues with migration:
- Join our [Discord](https://discord.gg/hjKcHavRjT) for support
- Report bugs on [GitHub Issues](https://github.com/iM5LB/relisheconomy/issues)
- Check the [Documentation](https://im5lb.github.io/relisheconomy) for detailed guides

---

**Note**: This changelog covers all changes made during the recent development session. For a complete version history, see the Git commit log.
