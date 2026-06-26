# Health Chat Bot

A comprehensive health information chatbot that provides details on diseases, symptoms, treatments, preventions, global disease outbreaks, and vaccination schedules. It interacts with users over WhatsApp, supporting multiple Indian regional languages with real-time translation capabilities.

## Tech Stack & Platforms

- **Flask**: The backend framework driving the core application logic and webhooks.
- **Dialogflow**: Google's NLU platform used for NLP, detecting user intents, and extracting entities (such as specific diseases).
- **Twilio**: Used for the WhatsApp webhook integration to send and receive messages with users.
- **Render**: The cloud hosting platform to deploy and serve the web application online.
- **GitHub**: Used for version control, cloud hosting of the source code, and CI/CD pipelines.
- **PostgreSQL**: Used for persistent context and session memory storage.

## Features

- **Multilingual Support**: Automatically detects and translates queries in Indian regional languages (Hindi, Telugu, Tamil, Kannada, Bengali, Marathi, Gujarati, Malayalam, Urdu, Punjabi, Odia, Kashmiri) into English for Dialogflow processing, and translates the response back to the user's native language.
- **Disease Information**: Retrieves overviews, symptoms, treatments, and prevention methods by scraping World Health Organization (WHO) fact sheets dynamically.
- **Outbreak News**: Connects to the WHO Outbreak API to report the latest global disease outbreaks.
- **Vaccination Schedules**: Calculates dates for the Polio vaccination schedule based on a user's date of birth.
- **Persistent Memory**: Remembers user contexts, recent queries, and language preferences across sessions using a PostgreSQL database (or an in-memory fallback).

## Environment Variables

Ensure the following environment variables are configured for deployment on Render:
- `DIALOGFLOW_PROJECT_ID`
- `GOOGLE_CREDENTIALS_JSON`
- `DATABASE_URL` (PostgreSQL)

## Local Development

```bash
# Install dependencies
pip install -r requirements.txt

# Start the application
python app.py
```