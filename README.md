# Class Routine Bot

A Node.js bot that automatically sends class routine updates to Telegram using Google Sheets as the data source and cron jobs for scheduling.

## Features

- 📅 Fetches class routine from Google Sheets
- 💬 Sends routine updates to Telegram group/chat
- ⏰ Schedules messages using cron jobs
- 📝 Optional to-do list integration from another Google Sheet
- 🔐 Supports multiple credential configuration methods
- 🌐 Lightweight and easy to deploy

## Prerequisites

- Node.js (v14 or higher)
- Telegram Bot Token (from [@BotFather](https://t.me/botfather))
- Google Service Account credentials (for Google Sheets API access)
- Google Sheet with class routine data
- Telegram Chat ID where messages will be sent

## Installation

1. Clone the repository:
```bash
git clone https://github.com/arshadziban/class_routine_bot.git
cd class_routine_bot
```

2. Install dependencies:
```bash
npm install
```

## Configuration

### Environment Variables

Create a `.env` file in the project root with the following variables:

```env
# Telegram Configuration
BOT_TOKEN=your_telegram_bot_token
CHAT_ID=your_telegram_chat_id

# Google Sheets Configuration
SHEET_URL=https://docs.google.com/spreadsheets/d/YOUR_SHEET_ID/edit
SHEET_RANGE=Sheet1!A:Z

# Optional: To-do List Sheet
TODO_SHEET_URL=https://docs.google.com/spreadsheets/d/YOUR_TODO_SHEET_ID/edit
TODO_SHEET_RANGE=Sheet1!A:Z

# Google Credentials (one of the following methods)
GOOGLE_CREDENTIALS_FILE=./credentials.json
# OR
GOOGLE_CREDENTIALS='{"type":"service_account","project_id":"...","private_key":"..."}'
# OR individual env variables
GOOGLE_TYPE=service_account
GOOGLE_PROJECT_ID=your_project_id
GOOGLE_PRIVATE_KEY_ID=your_key_id
GOOGLE_PRIVATE_KEY=your_private_key
GOOGLE_CLIENT_EMAIL=your_service_account_email
GOOGLE_CLIENT_ID=your_client_id
GOOGLE_AUTH_URI=https://accounts.google.com/o/oauth2/auth
GOOGLE_TOKEN_URI=https://oauth2.googleapis.com/token
GOOGLE_AUTH_PROVIDER_X509_CERT_URL=https://www.googleapis.com/oauth2/v1/certs

# Optional: Test Trigger Token
TEST_TRIGGER_TOKEN=your_test_token
```

### Setting Up Google Credentials

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new service account
3. Generate a JSON key file
4. Save it as `credentials.json` or set `GOOGLE_CREDENTIALS_FILE` environment variable

### Getting Telegram Credentials

1. Chat with [@BotFather](https://t.me/botfather) on Telegram
2. Create a new bot and get the **Bot Token**
3. Get your **Chat ID** by sending a message to your bot and checking the updates (or use a bot like [@userinfobot](https://t.me/userinfobot))

## Usage

### Start the bot:
```bash
npm start
```

### Run tests:
```bash
npm test
```

## How It Works

1. The bot reads class routine data from a Google Sheet
2. Parses the schedule based on the day of the week
3. Uses node-cron to schedule messages at specified times
4. Sends formatted messages to the configured Telegram chat
5. Optionally integrates with a to-do list from another Google Sheet

## Project Structure

```
class_routine_bot/
├── server.js           # Main bot logic
├── package.json        # Project dependencies
├── credentials.json    # Google API credentials (not tracked in git)
├── .env                # Environment variables (not tracked in git)
├── .gitignore          # Git ignore rules
└── README.md           # This file
```

## Dependencies

- **dotenv** - Load environment variables from .env file
- **googleapis** - Google APIs client library
- **node-cron** - Cron job scheduler
- **http/https** - Built-in Node.js modules for HTTP/HTTPS requests

## Security Notes

- Never commit `credentials.json` or `.env` files to version control
- Use environment variables for sensitive information
- Store credentials securely on your hosting platform
- Restrict Google Service Account permissions to only needed scopes

## Troubleshooting

### "SHEET_URL missing" error
- Ensure `SHEET_URL` is set in your `.env` file
- Verify the Google Sheet URL format

### "BOT_TOKEN missing" error
- Ensure `BOT_TOKEN` is set in your `.env` file
- Verify the token from [@BotFather](https://t.me/botfather)

### Google credentials not loading
- Check that `credentials.json` exists or `GOOGLE_CREDENTIALS_FILE` points to it
- Verify the JSON format is correct
- Ensure the service account has access to the Google Sheet

### Messages not sending
- Verify the `CHAT_ID` is correct
- Check Bot Token permissions
- Ensure the bot has been added to the Telegram chat

## Contributing

Feel free to fork this project and submit pull requests for any improvements.

## License

ISC

## Author

arshadziban

## Support

For issues and questions, please open an issue on the [GitHub repository](https://github.com/arshadziban/class_routine_bot/issues).
