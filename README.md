# Close Reader

A browser-based tool for close textual reading and AI-assisted annotation. Pick a reading, highlight passages, ask an LLM about them — annotations save in your browser, no account required.

**Features:**

- A growing library of readings: Gandhi's *Hind Swaraj*, the *Analects* of Confucius, Bryant's *Thanatopsis*, Plato's *Allegory of the Cave*, Ibsen's *A Doll's House* — with more on the way
- Six UI languages: English, Spanish, Greek (Modern), Chinese, Hindi, Norwegian — and each reading carries its own per-language translations
- AI annotations from many providers: Anthropic Claude, Google Gemini, Groq, OpenAI, DeepSeek — or run a local model with Ollama / LM Studio / llama.cpp
- Highlight a passage (yellow) or ask a question about it (blue) — both save to the margin column
- Auto-save per reading via `localStorage`; export / import all notes as JSON for backup
- API keys live only in your browser — never sent to any server we control
- Single HTML file, zero backend, MIT licensed

## Usage

Open: **[https://ohiomathteacher.github.io/close-reader/allegory-reader-v2.html](https://ohiomathteacher.github.io/close-reader/allegory-reader-v2.html)**

1. Pick a reading from the dropdown at the top of the page.
2. Select any passage in the text.
3. **Highlight** it (yellow) to mark a passage, or **Ask LLM** (blue) to attach a question.
4. To enable Ask LLM, click the **AI** button at the top right and pick a model from the **Local**, **$0** (free), or **Pay** tab.
5. Notes auto-save per reading. Use **Export** / **Import** to back them up or move them between browsers.
6. Use the language toggles to switch between the reading's available translations.

## AI Providers

The AI modal groups providers into three tabs:

- **Local** — models running on your own machine. No network calls leave the browser.
- **$0** — cloud providers with free tiers, no credit card required.
- **Pay** — cloud providers that need a billing-attached account.

You can configure several providers and switch between them per question.

### Local — Ollama, LM Studio, llama.cpp

Close Reader probes the well-known localhost ports when the AI modal opens and shows any detected servers as one-click tiles:

| Server | Default URL |
| --- | --- |
| Ollama | `http://127.0.0.1:11434` |
| LM Studio | `http://127.0.0.1:1234` |
| llama.cpp / Athena shim | `http://127.0.0.1:8765` |

**Setup (Ollama, easiest):**

1. Install from [ollama.com](https://ollama.com).
2. Pull a model in a terminal: `ollama pull llama3.2` (or `gemma3:27b`, `qwen2.5:14b`, etc.).
3. Open Close Reader. The AI modal's **Local** tab should show your Ollama server with its installed models. Click a model tile to select it.

**Setup (LM Studio):**

1. Install from [lmstudio.ai](https://lmstudio.ai).
2. Download a model from inside LM Studio.
3. Start the local server (Developer → "Start Server"). Default port is 1234.
4. Open Close Reader's AI modal — LM Studio appears under **Local**.

**Setup (other OpenAI-compatible local server):**

1. Click **+ Add local server** in the **Local** tab.
2. Paste the base URL (e.g. `http://127.0.0.1:8080`).
3. Pick a model from the list it returns.

Notes: nothing is auto-saved — you always pick the model. Endpoints you add are stored in `localStorage`.

### $0 — Google Gemini (Free)

- Model: `gemini-2.5-flash`
- Cost: Free up to generous daily limits
- **How to get a key:**
  1. Visit [aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
  2. **Important:** Use a **personal Gmail account**, not a school/organization account — many G-Suite accounts have the service disabled.
  3. Click **Create API Key** → "Create in new project"
  4. Copy the key (starts with `AIza`)
  5. Paste into the Gemini section in Close Reader's AI modal and click **Save**
- **Notes:** Best choice for students. No credit card required.

### $0 — Groq (Free)

- Model: Llama 3.3 70B (`llama-3.3-70b-versatile`)
- Cost: Free with rate limits; very fast inference
- **How to get a key:**
  1. Visit [console.groq.com](https://console.groq.com)
  2. Sign up with any email
  3. Open **API Keys** → **Create API Key**
  4. Copy the key (starts with `gsk_`)
  5. Paste into the Groq section and click **Save**
- **Notes:** Good alternative if Google Workspace is blocked at your school.

### Pay — Anthropic Claude

- Model: Claude Sonnet 4 (`claude-sonnet-4-20250514`)
- Cost: Paid (bring your own API key); excellent reasoning
- **How to get a key:**
  1. Visit [console.anthropic.com](https://console.anthropic.com)
  2. Sign up or log in; set up billing
  3. Go to **API Keys** → **Create Key**
  4. Copy the key (starts with `sk-ant-`)
  5. Paste into the Anthropic section and click **Save**
- **Notes:** Anthropic typically offers free trial credits. Roughly $0.10–$0.30 per question depending on length.

### Pay — OpenAI

- Model: `gpt-4o`
- Cost: Paid (bring your own API key)
- **How to get a key:**
  1. Visit [platform.openai.com](https://platform.openai.com)
  2. Sign up or log in; add a payment method under **Billing**
  3. Go to **API Keys** → **Create new secret key**
  4. Copy the key (starts with `sk-`)
  5. Paste into the OpenAI section and click **Save**

### Pay — DeepSeek

- Model: `deepseek-chat`
- Cost: Paid, very inexpensive per token
- **How to get a key:**
  1. Visit [platform.deepseek.com](https://platform.deepseek.com)
  2. Sign up and top up a small amount of credit
  3. Open **API Keys** → **Create new API key**
  4. Copy the key
  5. Paste into the DeepSeek section and click **Save**

### No AI

You can use Close Reader entirely without AI. Highlight passages, take margin notes, and export them as JSON — all offline, all local.

## API Key Security

**Your keys are safe:**

- Stored **only in your browser** via `localStorage`
- **Never** transmitted to any server we control
- **Only sent directly** to the provider you chose (Anthropic, Google, Groq, OpenAI, DeepSeek), or to `127.0.0.1` for local models
- The app is a single open-source HTML file — you can read every line yourself

**Best practices:**

- Use a personal email account for cloud keys, not your school or work account
- Don't share screenshots with keys visible
- Regenerate or revoke a key from the provider's dashboard if it leaks
- Set spending limits on paid providers

## Troubleshooting

**"Invalid API Key" error?**

- Confirm you copied the whole key (no leading/trailing whitespace, no cut-off characters)
- Gemini: verify you're using a personal Gmail, not a school account
- Regenerate the key in the provider's dashboard and re-save

**Key not saving?**

- Check that your browser allows `localStorage` (private/incognito browsing often disables it)
- Try a normal browser window; clear cache if needed

**Local model not detected?**

- Confirm the server is running (`curl http://127.0.0.1:11434/api/tags` for Ollama, `curl http://127.0.0.1:1234/v1/models` for LM Studio)
- If you use a non-default port, add it via **+ Add local server** in the AI modal

**Notes disappeared?**

- Notes are scoped per reading and per browser. Switching browsers or clearing site data will lose them — use **Export** regularly to back up to JSON.

**Can't get a key?**

- Use **No AI** to read and annotate locally
- Or run a local model with Ollama — completely free and private

## Technical

Pure frontend: one HTML file with embedded CSS and JavaScript. No backend, no database, no analytics, no cookies.

- Plato (*Allegory of the Cave*): Thomas Sheehan translation
- Each reading ships with its own translator credits and per-language sections
- Responsive layout: sticky header, independently scrolling text and margin columns
- Mobile-friendly reading dropdown

## Future Plans

Ideas on the roadmap — feedback and PRs welcome:

- **Load and translate PDFs on the fly** — drop in any PDF and get a clean, paragraph-segmented reading with on-demand translation into any of the UI languages
- **Read aloud** — text-to-speech for the current passage or the whole reading, with the option to use a local voice or a cloud TTS provider
- **An open-source bookshelf** — a curated library of coding texts, Project Gutenberg classics, public-domain primary sources, and other openly-licensed material, organized by subject area
- **Side-by-side parallel translations** — show two languages in adjacent columns rather than toggling between them, useful for language learners and translators
- **Shareable annotation sets** — export a reading + your margin notes as a single file a teacher or study group can import and discuss
- **Vocabulary glossary** — auto-build a personal glossary from the terms you ask the LLM about, exportable for flashcards or review

Close Reader is intentionally local-only: no backend, no accounts, no real-time chat. Localness is a feature — it keeps the focus on the reading.

## License

MIT — use, modify, and share freely. Attribution appreciated.

---

Built for close reading and active exploration across every content area.
