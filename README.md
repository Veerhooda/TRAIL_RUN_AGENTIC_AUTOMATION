🏞️ Trail Assistant Workflow with n8n

An n8n automation workflow designed to assist with planning and preparing for trail events. This workflow automatically checks your calendar for upcoming trail events, retrieves relevant weather data, recommends trail gear based on weather conditions, checks air quality index (AQI), and sends an email with all the information.

🌟 Features

Calendar Integration: Checks for upcoming trail events from Google Calendar.

Weather Forecast: Fetches weather data (e.g., temperature, wind, precipitation) for the event.

Recommendations: Pulls trail preparation recommendations from an Excel/Google Sheets document based on weather conditions.

Air Quality Index (AQI): Checks air quality and provides health advice based on AQI.

Automated Email: Sends a personalized email with all event details, weather, gear recommendations, and AQI information.



🛠️ Requirements

n8n: An open-source automation tool for workflow automation.

Google Calendar API: For fetching events from your Google Calendar.

Weather API: For retrieving weather data (e.g., OpenWeather).

Google Sheets: For reading gear recommendations and event data.

Gmail API: To send an email with the final trail information.

Setup Requirements

n8n Account

Install and set up n8n on your machine or use n8n.cloud. Follow this guide
 to install.

Google Cloud Project

Create a project in Google Cloud Console
.

Enable the Google Calendar API, Google Sheets API, and Gmail API for your project.

Create OAuth 2.0 credentials for both Google Calendar and Google Sheets.

Weather API Key

Register for an API key on your preferred weather service (e.g., OpenWeather
).

Configure Gmail API

Connect your Gmail account and enable sending emails via n8n.



⚙️ Workflow Setup

Google Calendar Node:

Add the Google Calendar node to search for upcoming trail events (events with keywords like “trail”, “hike”, etc.).

Make sure you have linked your Google Calendar API credentials.

Weather API Node:

Fetch weather details for the event location and date using the Weather API.

Configure the Weather API with your API key.

Data Source Node (Google Sheets):

Configure your Google Sheets credentials to access your trail recommendation sheet.

The sheet must contain columns for weather conditions (e.g., "Hot", "Rainy", "Windy") and associated gear/safety tips.

Weather AQI Node:

Use the Weather AQI API to retrieve the Air Quality Index for the trail event location.

Configure it with the same API key used for the weather service.

Gmail Node:

Use the Gmail node to send the final email with the event details, weather forecast, gear recommendations, and AQI report.



📝 Sample Workflow Diagram

Here’s an overview of how the workflow should look in n8n:

When chat message received (Trigger)
    |
    V
  AI Agent (Processes data & calls tools)
    |
    +--> Calendar (Fetch trail events)
    |
    +--> Weather API (Get weather for event)
    |
    +--> Data Source (Get recommendations based on weather)
    |
    +--> Weather AQI (Get AQI data for the location)
    |
    +--> Gmail (Send personalized email)



🏗️ Instructions for Configuring the Workflow in n8n

Trigger the Workflow:

Use the Trigger node to initiate the workflow based on incoming chat messages or custom triggers.

Configure Google Calendar:

Set the Google Calendar node to pull the next trail-related event.

Use keywords like "trail", "hike", "outdoor" to filter the events.

Weather Data:

Use the Weather API node to retrieve current weather conditions for the trail event location and date.

Google Sheets Integration:

The Google Sheets node should read from a sheet with recommendations based on the weather (gear, preparation tips).

Create a sheet where each weather condition maps to a specific recommendation (e.g., "Clear" -> "Light jacket", "Rainy" -> "Rain gear", etc.).

Air Quality:

Use the AQI node to get the air quality index for the event location. If AQI is unhealthy, provide health-related warnings.

Send the Email:

The Gmail node is triggered to send a detailed email summarizing the event, weather forecast, gear recommendations, and AQI data to the user’s email address.





🛠️ Troubleshooting
Common Errors:

"Client authentication failed":

This error usually occurs when Google credentials are incorrect. Ensure your OAuth credentials are correctly set up in n8n.

“Cannot read properties of undefined” in Gmail Node:

This error happens when the Gmail node is not receiving valid input (i.e., "to", "subject", or "body" is undefined). Ensure that the email body, subject, and recipient fields are filled before sending.

Google Sheets Errors:

Ensure your Google Sheets node is connected and has the correct Spreadsheet ID and Sheet name.

📧 Sample Email

Here’s an example of the email the system sends to the user:

Subject: Your Trail Preparation Summary – Weather, AQI, and Recommendations

Body:
Hi [User],

Here’s your personalized trail briefing for [Event Name] on [Date] at [Location]:





🌤 Weather Forecast:

Temperature: [Temp]

Condition: [Condition]

Wind: [Wind Speed]

UV: [UV Index]





🌫 Air Quality:

AQI: [AQI Number] ([AQI Level])

Notes: [AQI Health Recommendations]


🎒 Recommended Gear & Prep:

[Gear List]

[Safety Tips]

Let me know if you need further assistance with planning.

Best regards,
Your Trail Assistant

📘 Contributing

Feel free to open issues for bugs or request features. Pull requests are welcome if you’d like to add new functionalities or fix issues.
