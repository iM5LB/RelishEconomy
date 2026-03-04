# RelishEconomy Changelog

## Version 1.0.8-Beta (March 4, 2026)

### ✨ Added
- Added persistent player username storage (`player_name`) in balances for both SQLite and MySQL.
- Added built-in Portuguese language file: `lang/pt.yml`.

### 🔧 Improvements
- Database name validation now allows any practical name up to 64 chars. Rejects only unsafe cases: empty, leading/trailing spaces, control chars, /, \, or null char.
- Added automatic DB migration to create `player_name` on existing balances tables.
- Account load/join flow now refreshes and saves latest player usernames.
- Added new schema default key: `database.schema.balances.columns.player_name`.
- Added general performance and database/cache handling optimizations.

### 📘 Documentation
- Updated README and docs to include Portuguese language support.
- Updated database docs to describe stored identity fields (`uuid`, `player_name`, `discord_id`).
- Refined README top layout by moving support/store links under the top images.
- Improved README screenshot section headings for clearer and more consistent presentation.

---

## Version 1.0.7-Beta (March 1, 2026)

### ✨ **Added**
- Added hotbar selling command support:
  - `/sellhotbar` (alias: `/sellhb`)
  - `/re sell hotbar` (alias: `/re sell hb`)
- Added sold-item hover breakdowns to sell result messages.

### 🔧 **Improvements**
- Expanded sold-item hover behavior across command and GUI sell flows for more consistent feedback.
- Improved command availability handling for feature/license-based registration.

### 🛠️ **Fixed**
- Fixed command unregister behavior that could affect commands that should stay available.
- Fixed incorrect/garbled characters in multiple command output messages.

---

## Version 1.0.6-Beta (February 19, 2026)

### 🔧 Fixed
- Improved command registration handling for licensed and disabled features.
- Improved reload/restart behavior so feature-based commands update more reliably.
- General stability improvements around command availability checks.

---

## Version 1.0.5-Beta (February 16, 2026)

### 🔧 Fixed
- Towny bank deposit issue where `/t deposit <amount>` could take player money but town bank stayed at `$0`.
- Updated Towny/Vault economy flow so town bank balances now update correctly after deposits.

### ⚙️ **Configuration Updates**
- Added specific configuration options:
  - shop.yml -> `shop.enabled: true` (default)
  - prices.yml -> `sell.enabled: true` (default)
- Improved config synchronization so missing keys are added while keeping existing values.
- No structural config move is required for existing server files.

### 🧩 **Config Updater Improvements**
- Extended updater coverage beyond `config.yml`:
  - `shop.yml`
  - `prices.yml`
  - `gui.yml`
  - `lang/*.yml`
- Preserves existing values and only injects missing keys.

### 💾 **Backup Behavior**
- Backup files remain in the same directory as the source file.
- Updated backup naming format for clarity:
  - `<name>-backup-YYYYMMDD-HHMMSS.ext`
  - Collision-safe suffixes are appended when needed.

### 📊 **Metrics (bStats)**
- Added bStats integration.
- Added config toggle:
  - `metrics.enabled: true` (default)

---

## Version 1.0.4-Beta (February 15, 2026)

### 🔌 **Towny + Vault Compatibility**
- Added `loadbefore: [Towny]` in `plugin.yml` to improve startup ordering
- Improved Vault hook reliability:
  - Checks that Vault is enabled before registering provider
  - Re-registers safely if already hooked
  - Added startup retry hook attempts when Vault is late to initialize
- Added clearer startup logging for Vault provider registration

### 🏦 **Bank Account Support for Town/Nation Economy**
- Implemented full Vault bank API behavior for non-player accounts
- Added deterministic internal bank account IDs (name-based UUIDs) for stable persistence
- Enabled `hasBankSupport()` for proper Towny bank operations
- Added bank operations:
  - `createBank`, `deleteBank`, `bankBalance`, `bankHas`, `bankDeposit`, `bankWithdraw`
  - `isBankOwner`, `isBankMember`

### 🧩 **PlaceholderAPI Improvements**
- Fixed player placeholder requests failing for online/new accounts
- Improved placeholder parsing and compatibility:
  - Added leaderboard aliases: `leaderboard` and `top` (mapped to `baltop`)
  - Added formatted balance aliases via `balance_formatted`
- Improved raw balance output formatting:
  - Respects currency decimal settings
  - Uses stable locale formatting for numeric placeholders
- Prevented blank leaderboard placeholder outputs on cold cache/invalid positions by returning safe fallback values

### 📘 **Documentation**
- Updated `docs/PlaceholderAPI.md` with new alias placeholders and behavior notes
- Updated troubleshooting notes for placeholder account handling

---

## Version 1.0.3-Beta (February 10, 2026)

### 📝 **Documentation**
- **Complete Documentation Overhaul** - Fully updated documentation website
  - More clear and detailed information
  - Improved structure and navigation
  - Enhanced examples and guides
  - Better coverage of all features

### 🔄 **Real-Time Read Behavior**
- Background polling checks for external DB changes
- Only refreshes full balance data when `last_modified` changes
- Optimal for Discord/Web integrations that update balances out-of-band

*You need to replace Real-Time Sync with new config*
```yaml
database:
  # Real-time read mode (read from DB when balances change externally)
  # Recommended: true only if you manually edit DB and need instant visibility
  real-time-read: false
```

---

## Version 1.0.2-Beta (January 23, 2026)

### 🔧 **Bug Fixes**
- **New Player Balance** - Fixed issue where new players had their balance set instead of added to
  - Starting balance is now added to existing balance instead of overwriting it
  - Prevents accidental balance resets for returning players
  - Maintains proper balance accumulation across sessions

### 🛒 **Multi-Currency Shop Support**

This update adds full multi-currency support to the shop system, making it consistent with the sell functionality.
---

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




