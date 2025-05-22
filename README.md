


# ✨ AI-Powered Form Auto-Responder with n8n + ChatGPT

This project demonstrates how to create a fully automated system that:

1. Collects user input from a form
2. Processes the message using OpenAI’s ChatGPT
3. Sends a customized, intelligent reply to the user's email via Gmail

## 🚀 Overview

This workflow uses [n8n](https://n8n.io) (an open-source workflow automation tool) in combination with the OpenAI GPT API and Gmail integration to create a smart email responder. It can be used for contact forms, demo requests, or customer support.

## 📌 Features

- Form submission from any frontend (e.g., a website)
- Smart response generation using GPT-4
- Auto-reply via Gmail to the submitter
- Dynamic email templates
- Email extraction from message content (fallback-safe)

## 🛠️ Tech Stack

- [n8n](https://n8n.io)
- [OpenAI API](https://platform.openai.com/)
- [Gmail API](https://developers.google.com/gmail/api)
- Regex for extracting emails
- JSON-based email templating

## 🧱 How It Works

### 1. 📋 Form Submission

A form is created (e.g., via Webhook in n8n) that collects:

- First Name  
- Last Name  
- Email  
- Phone Number  
- Message  

Example form data:

```json
{
  "first name": "Harpreet",
  "last name ": "Singh",
  "Email": "example@gmail.com",
  "Number": "1234567890",
  "Message": "Hello! I'd like to know more about your services."
}
````

### 2. 🧠 GPT Response Generation

* The message is sent to GPT (via OpenAI node or HTTP request)
* A polite, context-aware reply is generated based on the submitted message

### 3. 📤 Auto-Email via Gmail

* The generated response is sent back to the user via Gmail
* A customizable email template is used

Example output:

```
Subject: Thank You for Reaching Out, Harpreet!

Hi Harpreet Singh,

Thank you for your message. I appreciate you reaching out.

Here’s a summary of what you submitted:

📧 Email: example@gmail.com  
📞 Phone Number: 1234567890  
📝 Message: Hello! I'd like to know more about your services.

Our team will get back to you shortly.

Warm regards,  
Harpreet
```

## 🔍 Highlights

* Dynamic email field fallback logic:

```js
{{ $json["message"]["content"].match(/[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}/)?.[0] || $json.Email }}
```

* Clean separation between extracted data and signature

## 📸 Screenshots

*(Add workflow screenshots, email preview, and form interface if available)*

## 🧪 How to Run

1. Clone this repo
2. Set up an n8n instance (self-hosted or cloud)
3. Import the workflow (`.json` export)
4. Set up environment variables/API keys:

   * `OPENAI_API_KEY`
   * Gmail OAuth credentials
5. Test using a form submission

## 📬 Future Improvements

* Store leads in a CRM (e.g., HubSpot, Notion, Airtable)
* Add file attachments
* Multi-language support
* Conversation threading

## 🙌 Credits

Built with ❤️ using [n8n](https://n8n.io), [OpenAI](https://openai.com), and [Gmail API](https://developers.google.com/gmail).

