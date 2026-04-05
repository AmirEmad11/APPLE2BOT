# Telegram Userbot Project

## Overview
This is a Python Telegram userbot that automatically handles join requests to a Telegram channel and sends welcome messages to new users.

## Core Components
- **bot.py**: Main bot script using Telethon library
- **requirements.txt**: Python dependencies (telethon, pyTelegramBotAPI, telethon-patch)
- **Procfile.bin**: Process configuration for deployment

## Architecture
- **Dual-client system**: User account + Bot account
- Uses Telethon-patch (enhanced Telethon) for Telegram API interaction
- **User client (@bet_store0)**: Monitors UpdatePendingJoinRequests events and auto-approves
- **Bot client (@betmanabot)**: Sends personalized welcome messages via private DM
- Separate entity resolution per client (prevents cross-session errors)
- Permission verification for both accounts

## Configuration Required
Environment secrets needed (stored securely in Replit Secrets):
- TELEGRAM_API_ID: Your Telegram API ID from my.telegram.org
- TELEGRAM_API_HASH: Your Telegram API hash from my.telegram.org  
- TELEGRAM_PHONE: Your phone number for authentication
- TELEGRAM_PASSWORD: Your Telegram 2FA password (if enabled)
- TELEGRAM_BOT_TOKEN: Your bot token from @BotFather
- TELEGRAM_CHANNEL: Target channel name or ID (can be set via /setchannel command)
- TELEGRAM_ADMIN_ID: Admin user ID (optional, auto-detected on first /start)

## Current Status
- ✅ **Dual-client system configured** - Ready for authentication
- ✅ **Security enhanced**: All credentials moved to encrypted secrets
- ✅ **Broadcast system fixed**: Fully functional with message forwarding
- ✅ **Smart channel detection**: Auto-finds channels by name or ID
- ✅ **Admin commands added**: /listchannels, /setchannel for easy management
- ✅ **State persistence fixed**: Proper saving/loading of user data
- ✅ **Bot authenticated and running**
- ✅ **November 1, 2025**: Major security and functionality updates completed
- ✅ **November 2, 2025**: Smart FOMO system and interactive buttons added
- ✅ **December 9, 2025**: Major stability fixes:
  - Fixed remote image download for daily plan messages
  - Robust apple game loop with error recovery
  - Follow-up task persistence across restarts
  - Non-blocking async image downloads

## Features Working
- ⚡ **Instant approval** of join requests via user client
- 🤖 **Dual-client architecture** - separate monitoring and messaging
- 💬 **Private welcome messages** from bot to new members
- 📢 **Broadcast system**: Send messages to all members with /broadcast command
- 🔍 **Smart channel search**: Auto-detect channels by name or ID
- ⚙️ **Admin commands**: 
  - /listchannels - View all available channels
  - /setchannel [ID/Name] - Set target channel dynamically
  - /broadcast - Send bulk messages to all members
  - /send_signal - Manually trigger Apple game signal
  - /stats - View bot statistics with conversion rate tracking
  - /status - Check bot health
  - /mark_registered [user_id] - Mark user as registered (stops FOMO messages)
- 🛡️ **Robust error handling** and permission checking
- 📊 **Detailed logging** with client-specific tracking
- 🎆 **Rich welcome message** with channel branding and motivation
- 🔒 **Channel isolation**: Each bot instance only responds to its configured channel
- 🚫 **Duplicate prevention**: 60-second deduplication window prevents duplicate welcomes
- ✨ **Single welcome path**: Disabled ChatAction handler to prevent duplicate messages
- 🔐 **Secure credentials**: All sensitive data stored in encrypted Replit secrets
- 🎯 **Smart FOMO System**: Automated follow-up messages at 30 minutes, 3 hours, and 24 hours
- 📈 **Conversion Tracking**: Monitors registered users and calculates conversion rates
- 🔘 **Interactive Buttons**: All messages include action buttons (Registration, Tutorial, Contact)
- ⏱️ **Scheduled Messages**: FOMO messages stop automatically when user registers
- 🧹 **Memory Management**: Automatic cleanup of completed tasks to prevent memory leaks

## Deployment
- ✅ **Replit Environment Setup Complete**
- ✅ Python 3.11 installed with all dependencies
- ✅ Workflow configured as console application
- ✅ VM deployment target configured for persistent operation
- ✅ No frontend component - console-only application
- ✅ Bot running and operational in development
- ✅ Ready for production deployment

## Replit Configuration
- **Language**: Python 3.12
- **Dependencies**: telethon==1.27.0, pyTelegramBotAPI==4.12.0, telethon-patch, pytz, requests
- **Workflow**: "Telegram Bot" - runs `python bot.py`
- **Output**: Console (shows bot logs and status)
- **Deployment**: VM target for persistent operation

## Important Notes
- The bot reads credentials from `config.py` (hardcoded) or environment variables as fallback
- Session files (`session_bot.session`, `session_user_*.session`) must be valid for the configured accounts
- The bot will exit if the target channel is not accessible by the user account
- To run fully: ensure the Telegram user account has joined/admin access to the target channel
- The channel ID in `config.py` (`CHANNEL_IDENTIFIER`) must match an accessible channel