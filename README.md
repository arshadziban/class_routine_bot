# Class Routine Bot

Automated Telegram bot that sends class schedules from Google Sheets using scheduled cron jobs.

## Features

- Fetches class routine from Google Sheets
- Sends scheduled updates to Telegram
- Cron-based message scheduling
- Optional to-do list integration
- Multiple credential configuration methods

## Prerequisites

- Node.js v14+
- Telegram Bot Token
- Google Service Account credentials
- Google Sheet with class data

## Installation

```bash
git clone https://github.com/arshadziban/class_routine_bot.git
cd class_routine_bot
npm install
```

## Configuration

Create a `.env` file:

```env
BOT_TOKEN=your_telegram_bot_token
CHAT_ID=your_chat_id
SHEET_URL=https://docs.google.com/spreadsheets/d/YOUR_SHEET_ID/edit
SHEET_RANGE=Sheet1!A:Z
GOOGLE_CREDENTIALS_FILE=./credentials.json
```

## Setup

1. **Google Credentials**: Download service account JSON from [Google Cloud Console](https://console.cloud.google.com/) and save as `credentials.json`
2. **Telegram Bot**: Create bot via [@BotFather](https://t.me/botfather)
3. **Telegram Chat ID**: Use [@userinfobot](https://t.me/userinfobot) to get your chat ID

## Usage

```bash
npm start
```

## Dependencies

- `dotenv` - Environment variables
- `googleapis` - Google Sheets API
- `node-cron` - Task scheduling

## Security

- Never commit `.env` or `credentials.json` files
- Use environment variables for credentials
- Restrict service account permissions

## License

ISC

---

For issues, visit the [GitHub repository](https://github.com/arshadziban/class_routine_bot/issues).
