# 🌍 Multilingual AI Content Scout (Man-in-the-Loop)

## 🤖 An n8n-powered AI Content Engine

This project is a sophisticated AI automation agent designed to transform raw ideas into a professional content ecosystem across multiple platforms and languages.

Developed by an AI Automation Engineer transitioning into the agentic AI space, this project demonstrates how modern automation tools can be combined into a powerful, production-ready content pipeline.

## 🚀 Key Features

- **Multilingual Generation:** Input a thought in any language and receive optimized content for English, Polish, and Spanish.
- **Triple-Format Output:**
  - Expert Longread (LinkedIn/Facebook)
  - Short Video Script (Reels/TikTok)
  - Engagement Post (Community Building)
- **AI Visuals:** Integrated DALL-E 3 node that generates unique illustrations tailored to the content's context.
- **Man-in-the-Loop Architecture:** No post goes live without human approval. The agent sends drafts to Telegram with interactive Approve/Decline buttons.
- **Cross-Workflow Data Bridge:** Google Sheets acts as a reliable data layer between the Generator and Moderator workflows, passing image URLs and multilingual post texts.
- **Auto-Publishing:** Confirmed posts are automatically published to LinkedIn 
and Facebook in the selected language via OAuth2 API.

## 🏗️ Architecture

The system consists of two separate n8n workflows:

**1. AI Content Master Generator**
- Triggered by a Telegram message
- Generates multilingual content via GPT-4o
- Creates a matching image via DALL-E 3
- Saves all data (texts + image URL) to Google Sheets
- Sends content previews to Telegram for review

**2. AI Content Master Moderator**
- Triggered by Telegram callback (Approve/Decline buttons)
- Reads post data from Google Sheets
- Dynamically selects the correct language based on user's choice
- Publishes the approved post to LinkedIn

## 🛠️ Technical Stack

- **Automation Engine:** n8n (Self-hosted/Local)
- **LLM:** OpenAI GPT-4o
- **Image Generation:** OpenAI DALL-E 3
- **Interface:** Telegram Bot API (Interactive Inline Buttons)
- **Data Bridge:** Google Sheets API
- **Publishing:** LinkedIn OAuth2 API, Facebook Graph API
- **Logic:** Advanced JSON parsing, multi-branching, cross-workflow data passing

## 👨‍💻 About the Author

Built during an intensive self-learning journey in AI automation. This project was co-developed with Claude (Anthropic) as a technical mentor and development partner.

## 📂 How to Use

1. Import both `.json` files into your n8n instance:
   - `AI Content Master Generator.json`
   - `AI Content Master - Moderator.json`
2. Set up your credentials:
   - Telegram Bot API
   - OpenAI API
   - Google Sheets OAuth2
   - LinkedIn OAuth2
   - Facebook Graph API
3. Create a Google Sheets spreadsheet with columns: `chat_id`, `image_url`, `timestamp`, `text_en`, `text_pl`, `text_es`
4. Update the Spreadsheet ID in both workflows
5. Activate both workflows and start creating content!
