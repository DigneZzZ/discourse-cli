# 🎯 disco - Discourse Launcher Management Tool

A convenient wrapper for managing Discourse with Telegram notifications support.

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Bash](https://img.shields.io/badge/bash-5.0+-orange)

## ✨ Features

- 🔄 **Container management** - rebuild, start, stop, restart
- 📊 **Monitoring** - status, logs, resource usage
- 💾 **Backup** - quick backup creation
- 📱 **Telegram notifications** - stay informed about all operations
- 🎨 **Beautiful interface** - colored output and clear messages
- ⚙️ **Flexible configuration** - .env file support

## 📦 Installation

### Quick install

```bash
# Download and install
curl -o disco https://raw.githubusercontent.com/yourusername/disco/main/disco
chmod +x disco
sudo mv disco /usr/local/bin/

# Verify installation
disco version
```

### Install from source

```bash
# Clone repository
git clone https://github.com/yourusername/disco.git
cd disco

# Install
sudo cp disco /usr/local/bin/
sudo chmod +x /usr/local/bin/disco
```

## ⚙️ Configuration

Create a `.env` configuration file in one of these locations:

- `~/.disco.env` (recommended)
- `/etc/disco/.env`
- Next to the script

```bash
# Copy example configuration
cp .env.example ~/.disco.env

# Edit settings
nano ~/.disco.env
```

### Example configuration

```bash
# Basic settings
DISCOURSE_PATH=/var/discourse
CONFIG_NAME=app

# Telegram notifications (optional)
TELEGRAM_BOT_TOKEN=1234567890:ABCdefGHIjklMNOpqrsTUVwxyz
TELEGRAM_CHAT_ID=-1001234567890
TELEGRAM_THREAD_ID=1
```

### Setting up Telegram notifications

1. **Create a bot:**
   - Message [@BotFather](https://t.me/BotFather)
   - Send `/newbot`
   - Follow instructions
   - Save the token

2. **Get Chat ID:**
   - Send any message to your bot
   - Visit: `https://api.telegram.org/bot<TOKEN>/getUpdates`
   - Find `"chat":{"id":...}`

3. **Get Thread ID (for groups with topics):**
   - Send a message to the desired topic
   - In getUpdates find `message_thread_id`

## 🚀 Usage

### Basic commands

```bash
# Full rebuild with notifications
sudo disco rebuild

# Quick rebuild (without launcher update)
sudo disco fast-rebuild

# Container management
sudo disco start
sudo disco stop
sudo disco restart

# Enter container
disco enter
```

### Monitoring and diagnostics

```bash
# Show status
disco status

# View logs
disco logs          # Last 100 lines
disco logs 500      # Last 500 lines

# Real-time monitoring
disco monitor

# Show disco configuration
disco show-config

# Show container configuration
disco config
```

### Maintenance

```bash
# Create backup
sudo disco backup                    # Automatic name
sudo disco backup my-backup-name     # Custom name

# Docker cleanup
sudo disco cleanup

# Update launcher
sudo disco update-launcher
```

### Utilities

```bash
# Test Telegram notifications
disco test-telegram

# Help
disco help

# Version
disco version
```

## 📱 Notification Examples

### When rebuild starts

```
🔧 Forum is going into maintenance

⏱ Expected time: ~10 minutes

We apologize for the temporary inconvenience.
```

### On successful completion

```
✅ Forum is back online!

⏱ Maintenance time: 7m 57s
🔖 Version: 3.2.0.beta4

Thank you for your patience! 🚀
```

### On error

```
❌ Forum update failed

⏱ Attempt duration: 3m 12s

⚠️ Administrator attention required!
Check logs: disco logs
```

## 🎨 Status Output Example

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 Discourse Status
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📦 Container: app
🟢 Status: Running
⏱  Uptime: Up 3 days
🔖 Version: 3.2.0.beta4
💻 CPU: 2.5%
🧠 Memory: 1.2GB / 4GB

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

## 🔧 Requirements

- **OS:** Linux (Ubuntu, Debian, CentOS, etc.)
- **Bash:** 4.0+
- **Docker:** 20.10+
- **curl:** for Telegram notifications (optional)
- **Discourse:** installed via official launcher

## 🤝 Contributing

Contributions are welcome! If you have ideas:

1. Fork the repository
2. Create a branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push to branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

## 📝 Roadmap

- [ ] Automatic backups before rebuild
- [ ] Monitoring integration (Prometheus/Grafana)
- [ ] CI/CD webhook support
- [ ] Rollback to previous version
- [ ] Forum health check
- [ ] Change history
- [ ] Multi-container support

## 🐛 Troubleshooting

If you encounter issues:

1. Check logs: `disco logs`
2. Check configuration: `disco show-config`
3. Create an [Issue](https://github.com/yourusername/disco/issues)

## 📄 License

MIT License - see [LICENSE](LICENSE) file

## 👤 Author

Created with ❤️ for the Discourse community

## 🌟 Acknowledgments

- [Discourse](https://www.discourse.org/) - for the excellent platform
- Community for feedback and suggestions

---

**Important:** Most commands require root privileges. Use `sudo` where necessary.

**Support:** If this tool was helpful, please ⭐ the repository on GitHub!
