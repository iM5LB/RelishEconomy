# RelishEconomy Changelog

## Version 1.1.1 (April 13, 2026)

### Added
- Premium ATM GUI:
  - `/re atm` command
  - Deposit tray for supported physical currency items
  - Withdraw flow with currency switching and amount controls
  - Configurable ATM block interaction via `config.yml`
- Expanded physical currency support:
  - Custom model data support per currency
  - Natural-source currency conversion for configured gameplay item sources
  - Currency items rewritten from the configured physical item template

### Changed
- README updated to reflect the current premium feature set more accurately.
- Premium markers in the README were normalized so premium-only sections and features are shown consistently from the start.
- ATM GUI layout was aligned more closely with the shop purchase workflow and cleaned up to remove duplicate controls.

### Fixed
- ATM GUI config/layout issues in `gui.yml`.
- ATM withdraw validation for integer currencies.
- Physical currency conversion timing across:
  - block drops
  - item spawn
  - item pickup
  - direct-to-inventory normalization paths
- Converted currency items now keep the configured display and metadata more reliably.
- Inventory reinsertion for converted currency items was adjusted to follow normal Bukkit stacking behavior more closely.

### Documentation
- README updated with ATM image placeholders and ATM configuration examples.
- README updated to include previously missing premium features and physical currency options.

---

## Version 1.1.0-Beta (March 17, 2026)

### Added
- Per-currency enable/disable toggle: `currencies.<name>.enabled` (default: `true`)
- Plugin now disables itself during startup if **zero** currencies are enabled (prevents broken/partial boot states).

### Fixed
- Baltop database spam reduction:
  - Skips invalid/blank UUID rows in the balances table instead of warning per row.
  - Emits a single throttled warning when invalid rows are detected.
- PlaceholderAPI formatting:
  - `%relisheconomy_balance_<currency>_<type>_<style>%` now supports the same formatting options as `formatted`
    (example: `full_plain` -> `1,250.00`).
- Baltop display name fallbacks for virtual/bank accounts:
  - Uses the stored account name when Bukkit has no player name (reduces `Unknown` entries).
  - Vault bank operations persist a friendly display name (Towny town/nation name when resolvable, otherwise bank name).

---

## Version 1.0.9-Beta (March 10, 2026)

This release is a large shop/GUI + configuration update, plus expanded physical currency customization and a safer config updater.

### **Added**
- SmartSpawner + Vault economy provider compatibility (SmartSpawner can use RelishEconomy as the economy)
- Shop favorites system:
  - `favorites.yml` storage
  - Favorites button in shop GUI and a dedicated Favorites category view
  - Favorite state messages: `shop.favorites.added`, `shop.favorites.removed`
  - Favorite items can render with a glow effect in the shop list
- New purchase flow GUI (Premium):
  - Clicking an item opens a buy GUI where players can increase/decrease quantity
  - Confirm purchase, cancel/back returns to the same category page
  - Favorite toggle from the purchase GUI
  - Confirm button can show player balance in its lore (configurable in `gui.yml`)
- `show-unpriced-items` option for shop browsing:
  - When enabled, items without a configured buy price can be shown as disabled instead of hidden
- Physical currency enhancements (per currency):
  - Optional crafting recipe support
  - Custom model data support for currency items
  - More customization options for physical currency item templates (material, name, lore, visual flags)
- Improved config restoration/merging (config updater):
  - Automatically restores missing bundled files: `config.yml`, `shop.yml`, `prices.yml`, `gui.yml`, `lang/en.yml`, `lang/ar.yml`, `lang/pt.yml`
  - Merges missing keys into existing YAML without wiping server edits
  - Automatic backups: `<file>-backup-YYYYMMDD-HHMMSS.ext`

### **Changed**
- Shop layout and defaults were reworked to match Creative inventory categories more closely (order, grouping, and paging).
- Operator/utility category is disabled by default in the bundled shop configuration.
- GUI sorting markers are configurable (set active/inactive symbols in `gui.yml`).
- `/re reload` now reloads GUI config, shop categories, and purchase flow state more reliably.
- Placeholder formatting adjustments:
  - Compact/plain formatted placeholders no longer force currency symbols when using the plain variants (use the symbol-specific placeholder for symbols).

### Fixed
- Many "invalid shop item key/material" warnings by hardening material/key parsing and validation for modern Minecraft versions.
- Premium command registration and tab-completion reliability after `/re reload` when license state is active.
- PlaceholderAPI rank placeholders no longer degrade to `N/A` after server uptime (baltop cache refresh + safer fallbacks).

### Documentation
- Updated plugin documentation pages to match the current 1.0.9 shop/GUI and currency features.
- Updated the repository `README.md` and docs site pages, and added/embedded screenshots from `docs/assets/`.

### **Notes**
- This update touches multiple configs. If you want to fully reset to defaults, you can delete the plugin config folder and restart; the config updater will recreate missing files and back up invalid ones.
- Some fixes listed above were done during development while implementing the new features, and are included in this release.

---

## Version 1.0.8-Beta (March 4, 2026)

### Added
- Added persistent player username storage (`player_name`) in balances for both SQLite and MySQL.
- Added built-in Portuguese language file: `lang/pt.yml`.

### Improvements
- Database name validation now allows any practical name up to 64 chars. Rejects only unsafe cases: empty, leading/trailing spaces, control chars, /, \, or null char.
- Added automatic DB migration to create `player_name` on existing balances tables.
- Account load/join flow now refreshes and saves latest player usernames.
- Added new schema default key: `database.schema.balances.columns.player_name`.
- Added general performance and database/cache handling optimizations.

### Documentation
- Updated README and docs to include Portuguese language support.
- Updated database docs to describe stored identity fields (`uuid`, `player_name`, `discord_id`).
- Refined README top layout by moving support/store links under the top images.
- Improved README screenshot section headings for clearer and more consistent presentation.

---

## Version 1.0.7-Beta (March 1, 2026)

### **Added**
- Added hotbar selling command support:
  - `/sellhotbar` (alias: `/sellhb`)
  - `/re sell hotbar` (alias: `/re sell hb`)
- Added sold-item hover breakdowns to sell result messages.

### **Improvements**
- Expanded sold-item hover behavior across command and GUI sell flows for more consistent feedback.
- Improved command availability handling for feature/license-based registration.

### **Fixed**
- Fixed command unregister behavior that could affect commands that should stay available.
- Fixed incorrect/garbled characters in multiple command output messages.

---

## Version 1.0.6-Beta (February 19, 2026)

### Fixed
- Improved command registration handling for licensed and disabled features.
- Improved reload/restart behavior so feature-based commands update more reliably.
- General stability improvements around command availability checks.

---

## Version 1.0.5-Beta (February 16, 2026)

### Fixed
- Towny bank deposit issue where `/t deposit <amount>` could take player money but town bank stayed at `$0`.
- Updated Towny/Vault economy flow so town bank balances now update correctly after deposits.

### **Configuration Updates**
- Added specific configuration options:
  - shop.yml -> `shop.enabled: true` (default)
  - prices.yml -> `sell.enabled: true` (default)
- Improved config synchronization so missing keys are added while keeping existing values.
- No structural config move is required for existing server files.

### **Config Updater Improvements**
- Extended updater coverage beyond `config.yml`:
  - `shop.yml`
  - `prices.yml`
  - `gui.yml`
  - `lang/*.yml`
- Preserves existing values and only injects missing keys.

### **Backup Behavior**
- Backup files remain in the same directory as the source file.
- Updated backup naming format for clarity:
  - `<name>-backup-YYYYMMDD-HHMMSS.ext`
  - Collision-safe suffixes are appended when needed.

### **Metrics (bStats)**
- Added bStats integration.
- Added config toggle:
  - `metrics.enabled: true` (default)

---

## Version 1.0.4-Beta (February 15, 2026)

### **Towny + Vault Compatibility**
- Added `loadbefore: [Towny]` in `plugin.yml` to improve startup ordering
- Improved Vault hook reliability:
  - Checks that Vault is enabled before registering provider
  - Re-registers safely if already hooked
  - Added startup retry hook attempts when Vault is late to initialize
- Added clearer startup logging for Vault provider registration

### **Bank Account Support for Town/Nation Economy**
- Implemented full Vault bank API behavior for non-player accounts
- Added deterministic internal bank account IDs (name-based UUIDs) for stable persistence
- Enabled `hasBankSupport()` for proper Towny bank operations
- Added bank operations:
  - `createBank`, `deleteBank`, `bankBalance`, `bankHas`, `bankDeposit`, `bankWithdraw`
  - `isBankOwner`, `isBankMember`

### **PlaceholderAPI Improvements**
- Fixed player placeholder requests failing for online/new accounts
- Improved placeholder parsing and compatibility:
  - Added leaderboard aliases: `leaderboard` and `top` (mapped to `baltop`)
  - Added formatted balance aliases via `balance_formatted`
- Improved raw balance output formatting:
  - Respects currency decimal settings
  - Uses stable locale formatting for numeric placeholders
- Prevented blank leaderboard placeholder outputs on cold cache/invalid positions by returning safe fallback values

### **Documentation**
- Updated `docs/PlaceholderAPI.md` with new alias placeholders and behavior notes
- Updated troubleshooting notes for placeholder account handling

---

## Version 1.0.3-Beta (February 10, 2026)

### **Documentation**
- **Complete Documentation Overhaul** - Fully updated documentation website
  - More clear and detailed information
  - Improved structure and navigation
  - Enhanced examples and guides
  - Better coverage of all features

### **Real-Time Read Behavior**
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

### **Bug Fixes**
- **New Player Balance** - Fixed issue where new players had their balance set instead of added to
  - Starting balance is now added to existing balance instead of overwriting it
  - Prevents accidental balance resets for returning players
  - Maintains proper balance accumulation across sessions

### **Multi-Currency Shop Support**

This update adds full multi-currency support to the shop system, making it consistent with the sell functionality.
---

### **New Features**
- **Per-Item Shop Currencies** - Shop now uses the same currency system as selling
- **Dynamic Currency Display** - Each item shows its price with the correct currency symbol
- **Consistent Currency Logic** - Shop and sell systems now work identically
- **Automatic Currency Detection** - Items automatically use their configured currency from `prices.yml`

### **Technical Changes**
- **ShopManager.java** - `getBuyCurrency(Material)` now returns per-item currencies
- **ShopGUI.java** - Updated to display and handle multiple currencies per item
- **ShopGUIListener.java** - Purchase transactions now use item-specific currencies
- **Balance Display** - Shows default currency balance (since multiple currencies can't be shown at once)

### **Configuration Updates**
- **shop.yml** - `buy-currency` setting is now deprecated (marked with comments)
- **Documentation** - Updated to reflect new multi-currency shop behavior
- **README.md** - Added deprecation notice for old shop currency setting

### **How It Works**
```yaml
# In prices.yml
prices:
  STONE: 0.5                    # Uses default currency (dollars) - shop shows $1.00
  DIAMOND: 
    price: 100
    currency: "coins"           # Shop shows ?200 (with 2.0x multiplier)
  EMERALD:
    price: 150  
    currency: "gems"            # Shop shows with gems symbol
```

### **Backward Compatibility**
- Existing configurations continue to work
- Single-currency setups remain unchanged
- No breaking changes to existing functionality

### **Migration Notes**
- The `buy-currency` setting in `shop.yml` is now ignored
- Shop items automatically use their currency from `prices.yml`
- No manual configuration changes required

---

## Version 1.0.1-Beta (January 22, 2026)

### **Major Feature Redistribution**

This update significantly restructures the premium/free feature distribution to provide more value in the free version while maintaining premium exclusivity for GUI and advanced features.

### **New Free Features**
- **Multi-Currency System** - Now available in free version with full support for custom currencies
- **Currency Exchange** - Exchange between different currencies with configurable rates
- **Advanced Sell Commands** - `/sellhand` and `/sellall` commands now free for all users
- **Advanced Transaction Logging** - Comprehensive transaction tracking and logging system

### **Premium-Only Features**
- **Shop GUI** - Interactive shop interface with category browsing
- **Sell GUI** - Drag-and-drop item selling interface  
- **Block Interactions** - Shop and sell block functionality
- **GUI Customization** - All GUI-related interactions and customizations
- **Physical Currency** - Withdraw currencies as physical items

### **Bug Fixes**
- Fixed missing message keys for `/shop help` command
- Added comprehensive help messages for shop commands in both English and Arabic

### **Technical Improvements**
- Updated license manager to properly handle new feature distribution
- Removed license checks from exchange and sell commands
- Added license validation for GUI and block interactions
- Improved debugging functionality and error handling

### **Configuration Updates**
- Updated language files with new shop help messages
- Enhanced message keys for better user experience
- Improved error messages and user feedback

### **Localization**
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




