# 📦 Installation Guide for disco

## Quick Installation (Recommended)

### Option 1: Using curl

```bash
# Download and install in one command
sudo curl -o /usr/local/bin/disco https://raw.githubusercontent.com/dignezzz/discourse-cli/main/disco && \
sudo chmod +x /usr/local/bin/disco

# Verify installation
disco version
```

### Option 2: Using wget

```bash
# Download and install
sudo wget -O /usr/local/bin/disco https://raw.githubusercontent.com/dignezzz/discourse-cli/main/disco && \
sudo chmod +x /usr/local/bin/disco

# Verify installation
disco version
```

## Installation from Source

```bash
# 1. Clone repository
git clone https://github.com/dignezzz/discourse-cli.git
cd disco

# 2. Install script
sudo cp disco /usr/local/bin/
sudo chmod +x /usr/local/bin/disco

# 3. Verify installation
disco version
```

## Configuration Setup

### Step 1: Create configuration file

```bash
# Create config directory (optional)
mkdir -p ~/.config

# Copy example configuration
curl -o ~/.disco.env https://raw.githubusercontent.com/dignezzz/discourse-cli/main/.env.example

# Or create manually
nano ~/.disco.env
```

### Step 2: Basic configuration

Minimum configuration for operation:

```bash
# ~/.disco.env
DISCOURSE_PATH=/var/discourse
CONFIG_NAME=app
```

### Step 3: Telegram Setup (Optional)

#### 3.1. Create Telegram Bot

1. Open Telegram and find [@BotFather](https://t.me/BotFather)
2. Send command `/newbot`
3. Follow instructions to create bot
4. Save the token (looks like `1234567890:ABCdefGHIjklMNOpqrsTUVwxyz`)

#### 3.2. Get Chat ID

**For private messages:**

```bash
# 1. Send any message to your bot
# 2. Run command (replace TOKEN with your bot token):
curl https://api.telegram.org/bot<TOKEN>/getUpdates

# 3. Find "chat":{"id":123456789} - this is your Chat ID
```

**For groups:**

```bash
# 1. Add bot to group
# 2. Send any message to group
# 3. Run command:
curl https://api.telegram.org/bot<TOKEN>/getUpdates

# 4. Find "chat":{"id":-1001234567890} - this is group Chat ID
```

#### 3.3. Get Thread ID (only for groups with topics)

```bash
# 1. Send message to desired topic in group
# 2. Run:
curl https://api.telegram.org/bot<TOKEN>/getUpdates

# 3. Find "message_thread_id":1 - this is Thread ID
```

#### 3.4. Add settings to .env

```bash
# Add to ~/.disco.env
TELEGRAM_BOT_TOKEN=1234567890:ABCdefGHIjklMNOpqrsTUVwxyz
TELEGRAM_CHAT_ID=-1001234567890
TELEGRAM_THREAD_ID=1  # Only for groups with topics
```

### Step 4: Verify configuration

```bash
# Show current configuration
disco show-config

# Test Telegram notifications
disco test-telegram
```

## Alternative Configuration Methods

### Using environment variables

```bash
# Add to ~/.bashrc or ~/.zshrc
export DISCOURSE_PATH=/var/discourse
export CONFIG_NAME=app
export TELEGRAM_BOT_TOKEN=your_token
export TELEGRAM_CHAT_ID=your_chat_id
export TELEGRAM_THREAD_ID=your_thread_id

# Reload configuration
source ~/.bashrc  # or source ~/.zshrc
```

### Global configuration (for all users)

```bash
# Create system-wide configuration
sudo mkdir -p /etc/disco
sudo nano /etc/disco/.env

# Add settings (without tokens!)
DISCOURSE_PATH=/var/discourse
CONFIG_NAME=app
```

## Verification

### Basic checks

```bash
# Check version
disco version

# Show help
disco help

# Show configuration
disco show-config

# Check Discourse status
disco status
```

### Checks with root privileges

```bash
# Test rebuild (will stop at confirmation)
sudo disco rebuild
# Press Ctrl+C to cancel

# Test cleanup
sudo disco cleanup
```

## Updating disco

### Automatic update

```bash
# Download and install latest version
sudo curl -o /usr/local/bin/disco https://raw.githubusercontent.com/dignezzz/discourse-cli/main/disco && \
sudo chmod +x /usr/local/bin/disco

# Check new version
disco version
```

### Update from Git

```bash
cd disco
git pull origin main
sudo cp disco /usr/local/bin/
disco version
```

## Uninstallation

```bash
# Remove script
sudo rm /usr/local/bin/disco

# Remove configuration (optional)
rm ~/.disco.env
sudo rm -rf /etc/disco
```

## Troubleshooting

### disco: command not found

```bash
# Check installation
which disco

# If not found, install again
sudo curl -o /usr/local/bin/disco https://raw.githubusercontent.com/dignezzz/discourse-cli/main/disco
sudo chmod +x /usr/local/bin/disco
```

### Permission denied

```bash
# Make file executable
sudo chmod +x /usr/local/bin/disco
```

### Telegram not working

```bash
# Check configuration
disco show-config

# Check token and Chat ID
disco test-telegram

# Check curl
which curl
```

## Additional Information

- 📖 [README.md](README.md) - Main documentation
- 📝 [CHANGELOG.md](CHANGELOG.md) - Version history
- 🐛 [Issues](https://github.com/dignezzz/discourse-cli/issues) - Report a problem

---

If you have any questions, create an [Issue](https://github.com/dignezzz/discourse-cli/issues) on GitHub.
