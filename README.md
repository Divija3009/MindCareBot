# Empower Mental Health Chatbot

A culturally sensitive AI-powered mental health chatbot using LangChain, GPT-4, Pinecone, and Flask. Developed as a master's capstone project at San José State University.
---
## Project Overview

This chatbot addresses global mental health challenges by:

- Offering culturally personalized responses  
- Supporting crisis detection and escalation  
- Integrating retrieval-augmented generation (RAG) using Pinecone  
- Enabling real-time voice/text interaction with TTS/STT  
- Logging sessions for therapist reviews and continuity  

## Architecture Overview
```
Frontend (React) <--> Flask Backend (LangChain + GPT-4) <--> PostgreSQL + Pinecone
                    ↳ Tools: PineconeSearch | WebSearch | ChatSummary | NearestTherapist
```

- Routing Agent: Dynamically selects tools or raw LLM  
- Tool-Enhanced Responses: Used for verified advice, cultural grounding, therapist lookup  
- Raw GPT-4 Responses: Used when personal empathy is more helpful  
- Dual Path Ranking: GPT-4 ranks both responses for final reply  

---
## Features

| Feature | Description |
|--------|-------------|
| Cultural Personalization | Tailors prompts based on selected user culture |
| RAG + Pinecone | Search vector DBs for CBT, PHQ-9, Indian context, SAMHSA |
| TTS & 🎙️ STT | Accessible speech input/output |
| Crisis Detection | Escalates emergencies with 988 lifeline + therapist map |
| Therapist Locator | Uses Google Maps API to suggest nearby help |
| Session Summaries | GPT-4 creates summaries for therapist review |
| Agent Tool Routing | LangChain agent selects tools dynamically |
| Secure Auth | Login/signup with hashed password & safe routing |

---

## Setup Instructions

###  1. Backend Setup (Flask)

```bash
cd backend
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
```

**Environment variables (.env):**
```ini
OPENAI_API_KEY=your_key
PINECONE_API_KEY=your_key
VITE_GOOGLE_MAPS_API_KEY=your_key
```

Start the API:
```bash
python api_for_db.py
```

---

### 2. Frontend Setup (React + Vite)

```bash
cd frontend
npm install
npm run dev
npm install rehype-raw
```

Make sure the Flask backend is running on `localhost:5001`.

---

## Testing

- 50 Test cases for Routing Agent – 88% accuracy  
- 50 Crisis Detection inputs – 94% accuracy  
- GPT-4 Evaluator scores (Empathy, Safety, Fluency)  
- Manual testing: TTS, STT, Therapist Locator  
- UI/UX tested across browsers and devices  

---

## Dataset Overview

| Dataset Type | Description | Pinecone Namespace |
|--------------|-------------|--------------------|
| 🇮🇳 Indian Cultural Context | Family, beliefs, collectivism | `indian_culture` |
| SAMHSA Guidelines | Clinical treatments & meds | `samhsa_guidelines` |
| Forum Chat Logs | Empathetic support examples | `chat_logs` |
| CBT Techniques | 15 strategies for mental health | `cbt_techniques` |
| PHQ-9 | 9-point depression scale | `phq9_intents` |
| Web-Scraped Info | WHO, NIMH, VeryWellMind | `web_anxiety`, etc. |

---

## Deployment Notes

- Currently tested on **localhost**
- Future-ready for deployment on **Heroku**, **Render**, or **AWS**
- Requires `.env` for OpenAI, Pinecone, and Google Maps API keys
---

