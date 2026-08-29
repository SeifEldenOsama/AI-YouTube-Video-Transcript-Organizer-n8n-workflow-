# AI YouTube Video Transcript Organizer

An **n8n AI automation workflow** that allows users to send a YouTube video link through Telegram, automatically extract its transcript, organize the content using an LLM, and return the structured result back to the user.

## 🚀 Features

* 📩 Receive YouTube URLs through Telegram
* 🎥 Automatically extract YouTube video transcripts
* ✅ Detect successful/failed transcript extraction
* 🤖 Use an LLM to organize transcript content
* 📝 Convert long transcripts into structured sections and headers
* ✂️ Split long responses into Telegram-safe message chunks
* 📤 Send the organized content back through Telegram
* ❌ Send a helpful error message when transcript extraction fails

## 🔄 Workflow

```text
Telegram Trigger
       ↓
Get Video Transcript
       ↓
Success Key
       ↓
      IF
    ↙     ↘
 Error     Success
  ↓          ↓
Error     Working Message
Message       ↓
           AI Content
           Organizer
               ↓
       Split Long Messages
               ↓
         Send Content
```

## 🧠 AI Content Organizer

The LLM receives the extracted transcript and is instructed to:

* Organize the content into meaningful headers and sections
* Preserve the original language of the video
* Produce a clean, readable message
* Avoid unnecessary symbols such as `#` and `*`

## 🛠️ Technologies

* **n8n** — Workflow automation
* **Telegram** — User interface
* **Supadata** — YouTube transcript extraction
* **OpenRouter** — LLM provider
* **JavaScript** — Message processing and splitting

## 📦 Main Nodes

| Node                  | Purpose                                 |
| --------------------- | --------------------------------------- |
| Telegram Trigger      | Receives the YouTube URL                |
| Get Video Transcript  | Extracts the video's transcript         |
| Success Key           | Determines whether extraction succeeded |
| IF                    | Routes successful and failed requests   |
| Error Message         | Notifies the user when extraction fails |
| Delay Message         | Tells the user processing has started   |
| Basic LLM Chain       | Organizes the transcript                |
| OpenRouter Chat Model | Provides the LLM                        |
| Split Long Messages   | Splits large responses                  |
| Send Content          | Sends the final result to Telegram      |

## ✂️ Long Message Handling

Telegram has a maximum message length, so the workflow automatically splits long AI-generated responses into smaller chunks before sending them.

The current implementation keeps each chunk below the Telegram limit:

```javascript
const maxLength = 4000;
```

## ⚙️ Setup

1. Install or run **n8n**.
2. Import the workflow JSON file.
3. Connect your Telegram Bot credentials.
4. Connect your Supadata API credentials.
5. Connect your OpenRouter credentials.
6. Configure the required nodes.
7. Activate the workflow.
8. Send a YouTube URL to your Telegram bot.

## 🔐 Credentials

The workflow requires credentials for:

* Telegram Bot
* Supadata API
* OpenRouter

**Do not commit API keys, tokens, or credentials to GitHub.**

## 💡 Example

**User sends:**

```text
https://www.youtube.com/watch?v=VIDEO_ID
```

**Workflow:**

```text
YouTube URL
    ↓
Transcript
    ↓
AI Organization
    ↓
Structured Content
    ↓
Telegram
```

## 📁 Project Structure

```text
AI-youtube-video-transcript-organizer/
│
├── AI youtube video transcript organizer.json
└── README.md
```

## 🎯 Purpose

This project demonstrates how **AI agents/LLM workflows can be combined with automation, APIs, data processing, and messaging platforms** to create a practical AI-powered application.

## 📨 Demo Telegram bot
https://t.me/youtube_video_transcript_132_bot

## 📄 License

This project is available for educational and personal use.
