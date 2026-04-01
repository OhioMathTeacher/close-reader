# Close Reader: Plato's Allegory of the Cave

A beautiful, interactive web app for close reading and annotating Plato's *Allegory of the Cave* (Republic VII, 514a–517a) in English or Modern Greek.

**Features:**
- 🤖 AI-powered annotations — Ask questions about any passage and get substantive answers
- 🎓 Four AI providers: Anthropic Claude, Gemini 2.0 Flash, Groq Llama, or no AI
- 📝 Margin notes with localStorage persistence
- 💾 Export/import notes as JSON for backup or transfer
- 🌍 Bilingual support (English & Modern Greek)
- 🎯 Zero code in the source — API keys stored only in your browser

## Usage

Visit: **[https://ohiomathteacher.github.io/close-reader/allegory-reader-v2.html](https://ohiomathteacher.github.io/close-reader/allegory-reader-v2.html)**

1. Select any passage in the text
2. Ask a question
3. Choose your AI provider (or none)
4. Notes are auto-saved to your browser
5. Export/import anytime to backup or share

## AI Providers

Choose one based on your needs:

### Anthropic Claude (Most Powerful)
- Model: Claude Sonnet 4
- Cost: **Paid** (bring your own API key)
- Reasoning: Excellent for nuanced philosophical questions
- **How to get a key:**
  1. Visit [console.anthropic.com](https://console.anthropic.com)
  2. Sign up or log in
  3. Go to **API Keys** → Create new key
  4. Copy the key (starts with `sk-ant-`)
  5. Paste into the "Anthropic Claude" section in Close Reader
  6. Click **Save**
- **Notes:** You'll need to set up billing, but Anthropic offers free trial credits. ~$0.10-0.30 per question depending on length.

### Gemini 2.0 Flash (Free via Google)
- Model: Google Gemini 2.0 Flash
- Cost: **Free** (up to 2,000 requests/day)
- Reasoning: Fast, capable, no credit card required
- **How to get a key:**
  1. Visit [aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
  2. **Important:** Use a **personal Gmail account**, NOT a school/organization account
     - School G-Suite accounts often have the service disabled
     - If you get an access error, use your personal Gmail instead
  3. Click **Create API Key**
  4. Select "Create in new project"
  5. Copy the key (starts with `AIza`)
  6. Paste into the "Gemini 2.0 Flash" section in Close Reader
  7. Click **Save**
- **Notes:** Best value for students. Completely free. Rate limit is **2,000 requests per day** (plenty for classroom use).

### Groq Llama 3.3 (Free, No Google Account)
- Model: Llama 3.3 70B
- Cost: **Free** (generous rate limits)
- Reasoning: Very fast, good for quick questions
- **How to get a key:**
  1. Visit [console.groq.com](https://console.groq.com)
  2. Sign up with **any email** (doesn't need to be Gmail)
  3. Go to your **API Keys** page
  4. Click **Create API Key**
  5. Copy the key (starts with `gsk_`)
  6. Paste into the "Groq (Llama 3.3)" section in Close Reader
  7. Click **Save**
- **Notes:** Excellent alternative if Google Workspace is blocked. No credit card required.

### No AI (Offline Mode)
- Use Close Reader without AI assistance
- Still get margin notes, auto-save, and export/import
- All text stays local — nothing sent anywhere

## API Key Security

**Your API keys are safe:**
- Keys are stored **only in your browser** using localStorage
- **Never** transmitted to our servers or any third party
- **Only sent directly** to the AI provider (Google, Anthropic, or Groq) when you submit a question
- The app source code is open-source — you can verify this yourself

**Best practices:**
- Use a personal email account (not your school/work account)
- Keep your API key private — don't share screenshots with keys visible
- You can always regenerate or delete a key from the provider's dashboard
- Each provider lets you set rate limits or disable keys anytime

## Troubleshooting

**"Invalid API Key" error?**
- Make sure you copied the full key (check for cut-off characters)
- If using Gemini: Verify you're using a personal Gmail, not a school account
- Regenerate the key in the provider's dashboard and try again

**Key not saving?**
- Check that your browser allows localStorage (private/incognito browsing may disable this)
- Try clearing browser cache and reloading

**Can't get a key?**
- Use the "No AI" option to read and annotate locally
- Or ask your teacher/librarian about accessing a shared API key

## Technical

Pure frontend (HTML/CSS/JavaScript). No backend, no databases, no data collection.

- Thomas Sheehan translation of Plato
- Comprehensive annotations keyed to the text
- Beautiful typographic design
- Fully responsive

## License

MIT — Use, modify, and share freely. Attribution appreciated.

---

Built for close reading in the humanities classroom.
