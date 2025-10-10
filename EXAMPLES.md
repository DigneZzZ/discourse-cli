# 📚 Usage Examples

Practical examples of using disco in different scenarios.

## 🎮 Interactive Menu Usage

### First Time User

```bash
# Just run disco
disco

# You'll see the interactive menu
# Navigate with ↑↓ arrows
# Press Enter on "📊 Show Status" to check your forum
```

### Regular Maintenance

```bash
# Start with sudo to have all permissions
sudo disco

# Navigate to:
# 1. Check status first
# 2. View logs if needed
# 3. Run cleanup monthly
# 4. Exit when done
```

### Quick Restart

```bash
# Launch menu
sudo disco

# Navigate down to "🔄 Restart Container"
# Press Enter
# Wait for completion
# Press Enter to return to menu
```

## 💻 Command-Line Usage

### Daily Operations

#### Check Forum Status

```bash
# Quick status check
disco status

# Output:
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
# 📊 Discourse Status
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
#
# 📦 Container: app
# 🟢 Status: Running
# ⏱  Uptime: Up 3 days
# 🔖 Version: 3.2.0.beta4
# 💻 CPU: 2.5%
# 🧠 Memory: 1.2GB / 4GB
```

#### View Recent Logs

```bash
# Last 100 lines (default)
disco logs

# Last 500 lines
disco logs 500

# Follow logs in real-time
disco logs 50
# Press Ctrl+C to exit
```

#### Monitor Resources

```bash
# Real-time monitoring
disco monitor

# Press Ctrl+C to exit
```

### Weekly Maintenance

#### Update Discourse

```bash
# Full rebuild with all updates
sudo disco rebuild

# Telegram notification will be sent automatically
# Forum will be down for ~10 minutes
# Another notification when it's back online
```

#### Fast Rebuild (No Launcher Update)

```bash
# Quicker rebuild without launcher update
sudo disco fast-rebuild

# Useful when you only changed configuration
```

#### Create Backup

```bash
# Automatic backup name with timestamp
sudo disco backup

# Custom backup name
sudo disco backup before-major-update
```

### Monthly Maintenance

#### Cleanup Docker Resources

```bash
# Free up disk space
sudo disco cleanup

# You'll see:
# - Current disk usage
# - What will be removed
# - Confirmation prompt
# - Disk usage after cleanup
```

#### Update Launcher

```bash
# Update Discourse launcher
sudo disco update-launcher

# Rebuild is recommended after update
sudo disco rebuild
```

## 🔧 Advanced Scenarios

### Troubleshooting

#### Container Won't Start

```bash
# 1. Check status
disco status

# 2. Check recent logs
disco logs 200

# 3. Try to start manually
sudo disco start

# 4. If still failing, check full logs
disco logs 1000 > discourse-error.log

# 5. Enter container for debugging
disco enter
```

#### High Memory Usage

```bash
# 1. Monitor resources
disco monitor
# Watch for a few minutes

# 2. If memory is too high, restart
sudo disco restart

# 3. Monitor again after restart
disco monitor
```

#### After Plugin Installation

```bash
# 1. Rebuild to apply plugin changes
sudo disco rebuild

# 2. Check if everything works
disco status
disco logs 100

# 3. If issues, enter container
disco enter
cd /var/www/discourse
./launcher logs app
```

### Configuration Changes

#### After Editing app.yml

```bash
# 1. Create backup first (just in case)
sudo disco backup before-config-change

# 2. Edit configuration
sudo nano /var/discourse/containers/app.yml

# 3. Rebuild to apply changes
sudo disco rebuild

# 4. Verify everything works
disco status
disco logs 100
```

#### Enabling Telegram Notifications

```bash
# 1. Edit configuration
nano ~/.disco.env

# Add:
# TELEGRAM_BOT_TOKEN=your_token
# TELEGRAM_CHAT_ID=your_chat_id

# 2. Test notifications
disco test-telegram

# 3. If successful, try with rebuild
sudo disco rebuild
# You should receive notifications!
```

### Automation & Scripts

#### Cron Job for Daily Status

```bash
# Add to crontab
crontab -e

# Check status every day at 9 AM
0 9 * * * /usr/local/bin/disco status >> /var/log/disco-status.log 2>&1
```

#### Backup Script

```bash
#!/bin/bash
# daily-backup.sh

# Create backup
sudo /usr/local/bin/disco backup daily-$(date +\%Y\%m\%d)

# Keep only last 7 days
find /var/discourse/shared/standalone/backups/default/ -name "daily-*.tar.gz" -mtime +7 -delete
```

#### Weekly Cleanup

```bash
# Add to crontab
crontab -e

# Cleanup every Sunday at 3 AM
0 3 * * 0 echo "yes" | sudo /usr/local/bin/disco cleanup >> /var/log/disco-cleanup.log 2>&1
```

## 🚀 Real-World Workflows

### New Administrator Workflow

```bash
# Day 1: Learn the tool
disco                    # Explore interactive menu
disco show-config        # Check configuration
disco status            # View forum status
disco logs 50           # Look at recent logs

# Day 2: Setup monitoring
nano ~/.disco.env       # Add Telegram settings
disco test-telegram     # Test notifications

# Day 3: First maintenance
sudo disco              # Use interactive menu
# Navigate to "💾 Create Backup"
# Then "🔄 Restart Container" to test

# Week 2: First update
sudo disco backup before-first-update
sudo disco rebuild      # Full update
```

### Emergency Response Workflow

```bash
# Forum is down!

# Step 1: Quick check
disco status

# Step 2: Review logs
disco logs 200

# Step 3: Try restart
sudo disco restart

# Step 4: Monitor
disco monitor

# Step 5: If still down, rebuild
sudo disco rebuild

# Step 6: Get help
disco logs 1000 > error-report.log
# Send error-report.log to support
```

### Planned Maintenance Workflow

```bash
# One day before:
# 1. Announce maintenance window
# 2. Create backup
sudo disco backup pre-maintenance-$(date +\%Y\%m\%d)

# Day of maintenance:
# 3. Update launcher
sudo disco update-launcher

# 4. Full rebuild (sends notification automatically)
sudo disco rebuild

# 5. Verify everything works
disco status
disco logs 100
disco monitor

# 6. Cleanup old resources
sudo disco cleanup

# After maintenance:
# 7. Monitor for 24 hours
disco status
disco logs
```

### Plugin Installation Workflow

```bash
# 1. Backup before changes
sudo disco backup before-plugin-$(date +\%Y\%m\%d)

# 2. Add plugin to app.yml
sudo nano /var/discourse/containers/app.yml

# Add to plugins section:
#   - git clone https://github.com/discourse/plugin-name.git

# 3. Rebuild
sudo disco rebuild

# 4. Check status
disco status

# 5. Enter container and enable plugin
disco enter
cd /var/www/discourse
rake admin:create_plugin[plugin-name]
exit

# 6. Verify logs
disco logs 100

# 7. If issues, restore backup
# (through Discourse admin panel)
```

## 📱 Telegram Integration Examples

### What You'll Receive

#### On Rebuild Start

```
🔧 Forum is going into maintenance

⏱ Expected time: ~10 minutes

We apologize for the temporary inconvenience.
```

#### On Successful Rebuild

```
✅ Forum is back online!

⏱ Maintenance time: 7m 57s
🔖 Version: 3.2.0.beta4

Thank you for your patience! 🚀
```

#### On Rebuild Failure

```
❌ Forum update failed

⏱ Attempt duration: 3m 12s

⚠️ Administrator attention required!
Check logs: disco logs
```

#### On Start/Stop/Restart

```
▶️ Forum started
⏹ Forum stopped
🔄 Forum is restarting...
✅ Forum restarted successfully
```

## 💡 Tips & Best Practices

### Interactive Menu

```bash
# Tip 1: Use sudo from the start
sudo disco              # All actions available

# Tip 2: Read confirmations carefully
# When asked "Type 'yes' to confirm:", actually type it

# Tip 3: Use 'q' for quick exit
# Instead of navigating to Exit

# Tip 4: Status is always visible
# No need to select "Show Status" just to check
```

### Command-Line

```bash
# Tip 1: Combine status with other commands
disco status && disco logs 50

# Tip 2: Redirect output for records
disco logs 500 > /tmp/discourse-logs.txt

# Tip 3: Use aliases for common tasks
alias dstatus='disco status'
alias dlogs='disco logs'
alias drestart='sudo disco restart'

# Tip 4: Backup before big changes
sudo disco backup && sudo disco rebuild
```

### Maintenance

```bash
# Tip 1: Schedule regular backups
# Every day at 2 AM
0 2 * * * sudo /usr/local/bin/disco backup daily-auto

# Tip 2: Monitor after updates
# Always check status and logs after rebuild

# Tip 3: Keep backups organized
# Use descriptive names: before-plugin, before-update, etc.

# Tip 4: Test recovery procedure
# Restore a backup in test environment to ensure it works
```

---

**Need more examples?** Open an [Issue](https://github.com/dignezzz/discourse-cli/issues) with your scenario!
