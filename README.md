<div align="center">
  <h1>🏥 Health Chat Bot</h1>
  <p>An intelligent, multilingual WhatsApp assistant delivering real-time health information, WHO data, and outbreak alerts directly to your phone.</p>
  
  [![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
  [![Flask](https://img.shields.io/badge/Flask-Framework-black?logo=flask)](https://flask.palletsprojects.com/)
  [![Dialogflow](https://img.shields.io/badge/Dialogflow-NLP-orange?logo=dialogflow)](https://cloud.google.com/dialogflow)
  [![Twilio](https://img.shields.io/badge/Twilio-WhatsApp-red?logo=twilio)](https://www.twilio.com/)
  [![Render](https://img.shields.io/badge/Render-Hosting-purple)](https://render.com/)
  [![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
</div>

<br />

## 📖 Table of Contents
- [Overview](#-overview)
- [Architecture & Tech Stack](#-architecture--tech-stack)
- [Key Features](#-key-features)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Environment Variables](#environment-variables)
- [Usage](#-usage)
- [Deployment](#-deployment)
- [License](#-license)

---

## 🔍 Overview
**Health Chat Bot** is a powerful conversational agent designed to bridge the gap in healthcare information accessibility. By integrating with WhatsApp, it provides users with instantaneous, accurate medical overviews, symptom checking, treatment guidelines, and preventative measures sourced dynamically from the World Health Organization (WHO).

The bot utilizes advanced Natural Language Processing (NLP) to understand user intent and supports seamless communication in over 12 Indian regional languages.

## 🏗 Architecture & Tech Stack

This project is built using a modern, scalable cloud-based architecture:

- **[Flask](https://flask.palletsprojects.com/)**: The core Python backend handling webhooks and application logic.
- **[Google Dialogflow](https://cloud.google.com/dialogflow)**: The NLU brain of the bot, trained to identify intents (e.g., `get_disease_overview`, `get_vaccine`) and extract medical entities.
- **[Twilio](https://www.twilio.com/)**: Serves as the communication bridge, routing messages between the user's WhatsApp and our backend server.
- **[PostgreSQL](https://www.postgresql.org/)**: Provides robust, persistent session memory to track user context, recent queries, and language preferences.
- **[Render](https://render.com/)**: The cloud infrastructure hosting the Flask application, ensuring high availability.
- **[GitHub](https://github.com/)**: Serves as the source of truth for version control, collaborative development, and seamless CI/CD integrations for cloud rendering.

## ✨ Key Features

- **🌐 Multilingual Translation Engine**: Automatically detects incoming languages and translates Indian regional languages (Hindi, Telugu, Tamil, Bengali, etc.) into English for NLP processing. Responses are seamlessly translated back into the user's native tongue.
- **🦠 Dynamic WHO Data Extraction**: Scrapes the latest WHO fact sheets in real-time to provide accurate overviews, symptoms, treatments, and prevention protocols.
- **🌍 Global Outbreak Alerts**: Connects directly to the WHO Outbreak API to report the most critical, up-to-date global health emergencies.
- **💉 Custom Vaccination Schedules**: Generates personalized Polio vaccination timelines based on user-provided birth dates.
- **🧠 Contextual Memory**: Maintains conversation state across messages using a PostgreSQL database, remembering the last queried disease to allow natural, flowing follow-up questions.

## 🚀 Getting Started

Follow these instructions to set up a local development environment.

### Prerequisites
- Python 3.8 or higher
- A [Twilio Account](https://www.twilio.com/) with a configured WhatsApp Sandbox
- A [Google Cloud Account](https://cloud.google.com/) with a Dialogflow project
- PostgreSQL (optional, for persistent DB storage)

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/radheshreddyyarram/Health_Chat_Bot.git
   cd Health_Chat_Bot
   ```

2. **Create a virtual environment (Recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. **Install the dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

### Environment Variables

Create a `.env` file in the root directory and add the following keys. These are necessary to connect the backend to Dialogflow and your database.

```env
# Dialogflow Configuration
DIALOGFLOW_PROJECT_ID=your_dialogflow_project_id
GOOGLE_CREDENTIALS_JSON={"type": "service_account", "project_id": "..."}

# Database (Optional - defaults to in-memory dictionary if omitted)
DATABASE_URL=postgresql://user:password@localhost:5432/healthdb

# Port (Optional)
PORT=5000
```

## 💻 Usage

Start the local server:
```bash
python app.py
```
*Note: To receive WhatsApp messages locally, you will need to expose your local server to the internet using a tool like [ngrok](https://ngrok.com/) and update your Twilio Webhook URL to point to `https://<your-ngrok-url>/whatsapp_webhook`.*

## ☁️ Deployment

This project is configured for easy deployment on **Render**. 
1. Connect your GitHub repository to Render.
2. Select "Web Service".
3. Use `pip install -r requirements.txt` for the build command.
4. Use `gunicorn app:app` for the start command.
5. Add the environment variables specified above in the Render dashboard.

## 📄 License
This project is licensed under the [MIT License](LICENSE).