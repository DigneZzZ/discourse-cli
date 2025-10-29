# Changelog

All notable changes to this project will be documented in this file.

## [1.2.0] - 2025-10-29

### 🔄 Added
- **Auto-update system** - Automatic version checking on startup (cached for 24 hours)
- **`disco self-update` command** - One-command update to latest version
- **Update notifications** - Visual notifications when new version is available
- Menu item "🔄 Update disco" in interactive menu (item 15)
- Update check when running `disco version` command
- Smart update mechanism with:
  - Download verification
  - Automatic sudo detection
  - Syntax validation before installation
  - Cache cleanup after successful update

### 🔧 Improved
- **Reliable version detection** - Changed primary method from API to direct file reading
  - Now reads from `/var/www/discourse/lib/version.rb` for 100% accuracy
  - API endpoint as fallback for compatibility
  - Fixed "unknown" version issue in Telegram notifications
- Better error handling in version detection
- One-line installation command in documentation

### 📝 Changed
- Version bumped to 1.2.0
- Menu now has 15 items (added self-update)
- Updated installation instructions (simplified to one command)
- Enhanced help text with self-update command

### 🐛 Fixed
- Discourse version now correctly displays in Telegram notifications
- Fixed version detection using more reliable method (`grep -E` instead of `grep -oP`)

### 📚 Documentation
- Updated README.md with v1.2.0 features
- Added update instructions
- Updated menu screenshots to show 15 items
- Updated roadmap with completed features

## [1.1.0] - 2025-10-10

### 🎮 Added
- **Interactive menu mode** - Launch `disco` without arguments for a user-friendly menu
- **Number-based navigation** - Just type 1-14 to select (more reliable than arrows)
- **API-based version detection** - Fast and reliable version display via `/about.json`
- Real-time container status and version display in menu header
- Visual indicators ⚠ for dangerous operations
- Safety confirmations for critical operations (rebuild, stop, cleanup)
- Type "yes" confirmation for dangerous actions
- Type '0' or 'q' to quit from menu

### 🔒 Improved
- Enhanced user safety with explicit "yes" confirmations for:
  - Full rebuild (with downtime warning)
  - Container stop (availability warning)
  - Docker cleanup (resource removal warning)
- Better visual feedback with numbered menu items
- Improved help text with interactive menu recommendation
- More reliable navigation (works in any terminal)
- Version detection with fallback mechanisms

### 🎨 Changed
- Default behavior: show interactive menu instead of help
- Version bumped to 1.1.0
- Updated GitHub URL in header
- Enhanced menu drawing with Unicode box characters
- Better status indicators (🟢 Running, 🔴 Stopped)

### 📝 Technical
- New functions: `draw_header()`, `draw_menu_item()`, `draw_separator()`
- New functions: `show_interactive_menu()`, `execute_menu_command()`
- Added menu state management with arrays
- Improved key input handling with ESC sequences

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2025-10-10

### Added

- Core Discourse launcher management functionality
- Telegram notification support
- Configuration via .env files
- `status` command for container monitoring
- `logs` command for viewing logs
- `backup` command for creating backups
- `cleanup` command for Docker resource cleanup
- `rebuild`, `start`, `stop`, `restart` commands
- `fast-rebuild` command for quick rebuilds
- `monitor` command for real-time resource monitoring
- `config` command for viewing container configuration
- `show-config` command for viewing disco configuration
- `test-telegram` command for testing notifications
- `update-launcher` command for launcher updates
- Colored console output
- Comprehensive documentation in README.md

### Changed

- No changes (initial release)

### Fixed

- No fixes (initial release)

### Removed

- No removals (initial release)

## [Unreleased]

### Planned

- Automatic backups before rebuild
- Monitoring integration (Prometheus/Grafana)
- CI/CD webhook support
- Rollback to previous version
- Forum health check
- Change history in Telegram
- Multi-container support
