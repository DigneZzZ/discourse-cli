# 🎮 Interactive Menu Features

## Overview

The interactive menu makes managing your Discourse instance as easy as playing a game! No need to remember commands - just navigate and select.

## Navigation

- **↑ / ↓** - Move up/down through menu items
- **Enter** - Select the highlighted option
- **q** - Quit the menu
- **Ctrl+C** - Cancel current operation

## Menu Layout

```text
╔════════════════════════════════════════════════════════════╗
║  🚀 Discourse Manager v1.1.0                              ║
║  📦 Container: app | Status: 🟢 Running                   ║
╚════════════════════════════════════════════════════════════╝

→ 📊 Show Status
  🔄 Restart Container
  📝 View Logs (last 100 lines)
  📺 Live Monitor
  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  🔧 Full Rebuild (with updates) (requires sudo) ⚠
  ⚡ Fast Rebuild (requires sudo)
  💾 Create Backup (requires sudo)
  🧹 Cleanup Docker Resources (requires sudo) ⚠
  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ▶️  Start Container (requires sudo)
  ⏸️  Stop Container (requires sudo) ⚠
  🐚 Enter Container Shell
  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  📥 Update Launcher (requires sudo)
  📱 Test Telegram Notifications
  ⚙️  Show Configuration
  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ❌ Exit

Use ↑↓ arrows to navigate, Enter to select, q to quit
```

## Visual Indicators

### Status Colors
- 🟢 **Green** - Container is running
- 🔴 **Red** - Container is stopped or not found

### Menu Item States
- **→ Cyan Bold** - Currently selected item
- **Gray Dimmed** - Available but not selected
- **(requires sudo)** - Action needs root privileges
- **⚠️  Yellow Warning** - Critical action requiring confirmation

### Separators
- **━━━━━━** - Groups related actions together

## Safety Features

### Confirmation Required

Critical operations require you to type "yes" to confirm:

#### 🔧 Full Rebuild
```text
⚠️  WARNING: 🔧 Full Rebuild (with updates)

This will:
  • Update Discourse to the latest version
  • Rebuild the entire container
  • Take approximately 10 minutes
  • Make the forum temporarily unavailable

Are you sure? Type 'yes' to confirm: _
```

#### ⏸️  Stop Container
```text
⚠️  WARNING: ⏸️  Stop Container

This will:
  • Stop the Discourse container
  • Make the forum unavailable until restarted

Are you sure? Type 'yes' to confirm: _
```

#### 🧹 Cleanup
```text
⚠️  WARNING: 🧹 Cleanup Docker Resources

This will:
  • Remove stopped containers
  • Remove unused Docker images
  • Free up disk space

Are you sure? Type 'yes' to confirm: _
```

### Sudo Detection

If you run the menu without sudo, actions requiring root privileges will show a warning:

```text
❌ This action requires root privileges

Please run: sudo disco

Press Enter to continue...
```

## Menu Actions

### Information & Monitoring
- **📊 Show Status** - Display container status, uptime, version, CPU and memory
- **📝 View Logs** - Show last 100 lines of container logs (with live follow)
- **📺 Live Monitor** - Real-time resource monitoring (CPU, memory, network, disk)
- **⚙️  Show Configuration** - Display disco settings (paths, Telegram config)

### Container Management
- **🔄 Restart Container** - Quick restart (no confirmation needed)
- **▶️  Start Container** - Start stopped container
- **⏸️  Stop Container** - Stop running container (requires confirmation)
- **🐚 Enter Container Shell** - Open bash shell inside container

### Maintenance
- **🔧 Full Rebuild** - Complete rebuild with Discourse updates (requires confirmation)
- **⚡ Fast Rebuild** - Quick rebuild without launcher update
- **💾 Create Backup** - Create backup with automatic timestamp
- **🧹 Cleanup** - Remove unused Docker resources (requires confirmation)
- **📥 Update Launcher** - Update Discourse launcher to latest version

### Utilities
- **📱 Test Telegram** - Send test notification to verify setup
- **❌ Exit** - Close the menu

## Return to Menu

After each action completes, you'll see:

```text
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Press Enter to return to menu...
```

This gives you time to read the output before returning to the menu.

## Tips

1. **Run with sudo** from the start if you plan to do administrative tasks:
   ```bash
   sudo disco
   ```

2. **Read confirmations carefully** - they explain exactly what will happen

3. **Use 'q' for quick exit** instead of navigating to Exit menu item

4. **Status is always visible** in the header - no need to select "Show Status" just to check if it's running

5. **For automation** or scripts, you can still use command-line mode:
   ```bash
   disco status
   disco logs 100
   ```

## Keyboard Shortcuts Summary

| Key | Action |
|-----|--------|
| ↑ | Move selection up |
| ↓ | Move selection down |
| Enter | Select/Execute |
| q or Q | Quit menu |
| Ctrl+C | Cancel operation |

## Advantages Over Command-Line Mode

✅ **No need to remember commands** - everything is visible  
✅ **Visual feedback** - see status at a glance  
✅ **Safer** - confirmations prevent accidents  
✅ **Faster** - navigate with arrows, no typing  
✅ **Discoverable** - all features are visible  
✅ **Beginner-friendly** - perfect for occasional use  
✅ **Still fast for experts** - arrow keys are quick  

## When to Use Command-Line Mode

- **Automation** - scripts and cron jobs
- **SSH with limited terminal** - some terminals don't support arrow keys well
- **Quick one-off commands** - faster to type `disco status` than launch menu
- **Remote execution** - piping commands or running via sudo with specific args

## Examples

### Quick Status Check (CLI)
```bash
disco status
```

### Interactive Session (Menu)
```bash
# Launch menu
disco

# Navigate with arrows, view status
# Check logs if needed
# Return to menu
# Exit when done
```

### Administrative Tasks (Menu with sudo)
```bash
# Launch with root privileges
sudo disco

# Now you can:
# - Rebuild
# - Start/Stop
# - Create backups
# - Cleanup
# All without additional prompts
```

---

**Pro Tip:** The interactive menu is especially useful when SSH'd into your server - it keeps you oriented and prevents mistakes!
