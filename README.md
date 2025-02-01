# AI Chatbot

This repository contains the source code for an AI-powered chatbot designed to interact via WhatsApp. It uses the WhatsApp API, OpenAI, and LangChain to receive, process, and respond to messages automatically.

## Features
- **Message reception via webhooks**: Uses Flask to set up an endpoint that receives WhatsApp messages from Meta for Developers.
- **Response generation with OpenAI**: Utilizes the OpenAI API to generate contextual responses.
- **Security and management with LangChain**: Implements LangChain to structure conversations and enhance security.
- **Automated response sending**: Uses the WhatsApp API with the requests library to respond to customers in real-time.

## Installation

### Prerequisites
Before getting started, make sure you have installed:
- Python 3.8 or higher
- An OpenAI account with credits
- Access to the WhatsApp API from Meta for Developers

### Installation Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/youruser/ai-chatbot.git
   cd ai-chatbot
   ```
2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Set up environment variables:
   ```bash
   export OPENAI_API_KEY="your-api-key"
   export WHATSAPP_ACCESS_TOKEN="your-whatsapp-token"
   export WEBHOOK_VERIFY_TOKEN="your-verification-token"
   ```
   On Windows, use:
   ```powershell
   $env:OPENAI_API_KEY="your-api-key"
   $env:WHATSAPP_ACCESS_TOKEN="your-whatsapp-token"
   $env:WEBHOOK_VERIFY_TOKEN="your-verification-token"
   ```

## Usage

### Webhook Configuration
1. Run the Flask server:
   ```bash
   python app.py
   ```
2. Set up the webhook in [Meta for Developers](https://developers.facebook.com/) using your server's public URL (you can use ngrok for local testing).

### Message Processing
- Flask receives the message via the webhook.
- OpenAI generates a response based on the received message.
- LangChain can be used to enhance conversation management and security.
- The response is sent to the user via the WhatsApp API.

### Sending Responses
Responses are sent using the `requests` library via the WhatsApp API.

Example code:
```python
import requests

def send_whatsapp_message(number, message):
    url = "https://graph.facebook.com/v16.0/me/messages"
    headers = {"Authorization": f"Bearer {WHATSAPP_ACCESS_TOKEN}", "Content-Type": "application/json"}
    data = {
        "messaging_product": "whatsapp",
        "to": number,
        "text": {"body": message}
    }
    response = requests.post(url, headers=headers, json=data)
    return response.json()
```

## Tools
- **Flask**: To configure webhooks and receive messages.
- **OpenAI API**: To process messages and generate responses.
- **LangChain**: To enhance security and conversation management.
- **Requests**: To send responses through the WhatsApp API.

## Contribution
If you want to contribute, open an issue or submit a pull request with improvements or new features.

## License
This project is under the MIT license. See the `LICENSE` file for more details.

