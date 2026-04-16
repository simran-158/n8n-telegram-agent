# n8n-telegram-agent
# Reposo Salon — Telegram Booking Bot

A Telegram bot built with n8n that handles appointment booking, cancellation, updates, and AI-powered customer Q&A for Reposo Salon.

## Features

- Book appointments with 11 service types
- Smart availability checking via Google Calendar
- Cancel bookings by phone number lookup
- Update/reschedule existing bookings
- AI-powered Q&A about salon services and hours
- Operating hours: 10 AM - 9 PM, Mon-Sat

## Prerequisites

### 1. Create Telegram Bot
1. Message @BotFather on Telegram
2. Send `/newbot`, name it "Reposo Salon"
3. Copy the bot token

### 2. Google Calendar
1. Create a calendar called "Reposo Salon Bookings" in Google Calendar
2. Note the calendar ID (Calendar Settings > Integrate calendar)

### 3. OpenRouter API Key
1. Sign up at https://openrouter.ai
2. Create an API key at https://openrouter.ai/keys

### 4. n8n Environment Variables

Set these environment variables in your n8n instance:

```
TELEGRAM_BOT_TOKEN=your_telegram_bot_token_here
OPENROUTER_API_KEY=your_openrouter_api_key_here
```

To set environment variables in n8n:
- **Docker:** Add `-e TELEGRAM_BOT_TOKEN=xxx -e OPENROUTER_API_KEY=xxx` to your docker run command
- **npm/self-hosted:** Export them in your shell before starting n8n, or add to `.env`
- **n8n Cloud:** Settings > Environment Variables

## Setup

1. Open your n8n instance
2. Create a new workflow (or import `workflow.json`)
3. **Telegram Trigger node:** Add a Telegram API credential with your bot token
4. **Google Calendar nodes:** Add a Google Calendar OAuth2 credential, then select the "Reposo Salon Bookings" calendar in each Google Calendar node
5. Verify environment variables are set (`TELEGRAM_BOT_TOKEN`, `OPENROUTER_API_KEY`)
6. Activate the workflow

## Testing

Send `/start` to your bot on Telegram to verify the welcome menu appears.

### Test Flows

1. **Book:** `/start` > Book Appointment > pick service > pick date > pick time > enter name > enter phone > confirm
2. **Services:** `/start` > Our Services > see list
3. **Cancel:** `/start` > Cancel Booking > enter phone > select booking > cancelled
4. **Update:** `/start` > Update Booking > enter phone > select booking > change date/service > confirm
5. **AI Chat:** `/start` > Ask a Question > type a question > get AI answer > type "menu" to exit

## Services

| Service | Duration |
|---------|----------|
| Haircut (Men) | 30 min |
| Haircut (Women) | 45 min |
| Hair Coloring | 90 min |
| Hair Styling / Blowout | 45 min |
| Manicure | 30 min |
| Pedicure | 45 min |
| Facial | 60 min |
| Cleanup / Threading | 20 min |
| Head Massage | 30 min |
| Full Body Massage | 60 min |
| Bridal Package | 180 min |
