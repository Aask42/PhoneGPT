# PhoneGPT

Welcome to PhoneGPT, a program I wrote for the Mile-High Wild West Hackin' Fest in Denver, CO Feb 5-7 2025. This program, once all services are set up, will allow you to use python to make phone calls with ChatGPT as your agent talking to the other side. 

NOTE: This is probably buggy and if you can't debug Python code you may not be able to get this working.

## Prerequisites

Before you begin, ensure you have the following installed:

- Python 3.9+
- Twilio Account
- ngrok Account
- OpenAI API Key

## How to use

- YOU WILL NEED THREE TERMINALS OPEN. 

- Clone this repo down
  - ```cd PhoneGPT``` 
- Create a virtual environment and install the right stuff
  - ```python3 -m venv venv```
  - ```. ./venv/bin/activate```
  - ```pip install -r requirements.txt```
- SET YOUR ENVIRONMENT VARIABLES
  - Copy the .env_template to .env
    - ```cp .env_template .env```
  - Update the values in .env to your values
- In your FIRST terminal, run your ngrok server
  - ```ngrok http localhost:5001```
  - Copy the .app URL that is output
- Access "https://console.twilio.com/" and log in
  - Click "Phone numbers"
  - Click "Manage"
  - Click "TwiML Apps"
  - Set up an app
    - Use your ngrok .app URL for these. Yes they should remain POST. 
- In your SECOND terminal your python script
  - ```python3 twilio_ai_chat.py```
- In your THIRD terminal
  - Activate your .env file
    - ```. ./venv/bin/activate```
    - run ```place_call("+18005555555)``` (Replace with your target number)
- You should now be able to see the conversation in ```voice_log.csv``` or in your SECOND terminal

## Account Setup Info

- On your Twilio account, once signed in and set up with a number, go to "https://console.twilio.com/" 
  - Click "Phone numbers"
  - Click "Manage"
  - Click "TwiML Apps"
  - Set up an app
    - NOTE: We will come back to this configuration once your ngrok server is running
    - You will need to set the URL in the app to be the ".app" url output by ngrok
- Set up an ngrok account
  - This is free for developers
