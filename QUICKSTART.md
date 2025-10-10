# 🚀 Quick Start Guide

Get started with disco in 5 minutes!

## Step 1: Install (30 seconds)

```bash
sudo curl -o /usr/local/bin/disco https://raw.githubusercontent.com/DigneZzZ/discourse-cli/main/disco && \
sudo chmod +x /usr/local/bin/disco
```

## Step 2: Verify (5 seconds)

```bash
disco version
# Output: disco v1.1.0
```

## Step 3: Try It! (10 seconds)

```bash
disco
```

You'll see:

```text
╔════════════════════════════════════════════════════════════╗
║  🚀 Discourse Manager v1.1.0                              ║
║  📦 Container: app | Status: 🟢 Running                   ║
╚════════════════════════════════════════════════════════════╝

→ 📊 Show Status
  🔄 Restart Container
  📝 View Logs (last 100 lines)
  ...
```

**That's it!** 🎉

## What You Can Do Now

### 🔍 Check Status

Navigate to **"📊 Show Status"** and press Enter:

```text
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 Discourse Status
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📦 Container: app
🟢 Status: Running
⏱  Uptime: Up 3 days
🔖 Version: 3.2.0.beta4
💻 CPU: 2.5%
🧠 Memory: 1.2GB / 4GB
```

### 📝 View Logs

Navigate to **"📝 View Logs"** to see what's happening:

```bash
# Shows last 100 lines of logs
# Press Ctrl+C to exit
```

### 🔄 Restart Forum

Navigate to **"🔄 Restart Container"** with sudo:

```bash
sudo disco
# Navigate to "🔄 Restart Container"
# Press Enter
# Wait for restart
# Done!
```

## Navigation Tips

- **↑↓** - Move between options
- **Enter** - Select option
- **q** - Quick exit
- **Ctrl+C** - Cancel operation

## When You Need Sudo

Some actions show **(requires sudo)**:

```text
  🔧 Full Rebuild (with updates) (requires sudo) ⚠
```

For these, run:

```bash
sudo disco
```

## Important Actions with Warnings ⚠️

Critical actions like **Rebuild**, **Stop**, and **Cleanup** require typing "yes" to confirm:

```text
⚠️  WARNING: 🔧 Full Rebuild (with updates)

This will:
  • Update Discourse to the latest version
  • Rebuild the entire container
  • Take approximately 10 minutes
  • Make the forum temporarily unavailable

Are you sure? Type 'yes' to confirm: _
```

Type **yes** (not y or Y) to proceed.

## Optional: Setup Telegram Notifications

Want notifications? Create `~/.disco.env`:

```bash
nano ~/.disco.env
```

Add:

```bash
TELEGRAM_BOT_TOKEN=your_bot_token_here
TELEGRAM_CHAT_ID=your_chat_id_here
```

Test it:

```bash
disco test-telegram
```

You'll receive:

```
🧪 Test message

✅ Notifications are working correctly!
🤖 disco v1.1.0
📅 2025-10-10 15:30:00
```

## Command-Line Alternative

Don't like menus? Use commands directly:

```bash
disco status          # Quick status
disco logs           # View logs
sudo disco restart   # Restart forum
sudo disco rebuild   # Full update
```

## Next Steps

1. ✅ **Explore the menu** - try different options
2. 📚 **Read [FEATURES.md](FEATURES.md)** - learn all features
3. 💡 **Check [EXAMPLES.md](EXAMPLES.md)** - see real workflows
4. 📱 **Setup Telegram** - get notifications
5. 🔧 **Create your first backup** - `sudo disco backup`

## Need Help?

- 📖 [Full Documentation](README.md)
- 🐛 [Report Issues](https://github.com/DigneZzZ/discourse-cli/issues)
- 💬 [Ask Questions](https://github.com/DigneZzZ/discourse-cli/discussions)

---

**Welcome to disco! 🎉**

You now have a powerful, user-friendly tool for managing your Discourse forum!
