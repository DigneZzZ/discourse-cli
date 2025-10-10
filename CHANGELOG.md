# Changelog

All notable changes to this project will be documented in this file.

## [1.1.0] - 2025-10-10

### 🎮 Added
- **Interactive menu mode** - Launch `disco` without arguments for a user-friendly menu
- Arrow key navigation (↑↓) for menu selection
- Real-time container status display in menu header
- Visual indicators for actions requiring sudo
- Safety confirmations for critical operations (rebuild, stop, cleanup)
- Type "yes" confirmation for dangerous actions
- Press 'q' to quit from menu
- Automatic separator skip in navigation

### 🔒 Improved
- Enhanced user safety with explicit confirmations for:
  - Full rebuild (with downtime warning)
  - Container stop (availability warning)
  - Docker cleanup (resource removal warning)
- Better visual feedback with new colors (cyan, magenta, bold, dim)
- Improved help text with interactive menu recommendation
- Menu shows which actions require root privileges

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
