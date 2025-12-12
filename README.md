# 📞 Hold My Spot
> **Your AI-Powered Assistant for Waiting on Hold**

**Hold My Spot** is a sophisticated full-stack application that leverages advanced Voice AI to handle phone calls on your behalf. Built on the scalable **Raindrop** serverless platform, it integrates **ElevenLabs** for realistic voice generation and speech-to-text transcription.

---

## ✨ Key Features

### 🤖 AI Voice Agent
- **Natural Speech Generation**: Uses ElevenLabs' advanced Text-to-Speech (TTS) models (`eleven_multilingual_v2`) to simulate human conversation.
- **Dynamic Voice Selection**: Support for multiple voice personas (e.g., Male/Female options).
- **Customizable Responses**: Generates speech dynamically based on user input.

### 🎙️ Voice Generator Platform
A dedicated workspace for testing and utilizing AI voice capabilities:
- **Text-to-Voice (TTS)**: Input any text and generate audio instantly using selected voice profiles.
- **Voice-to-Text (STT)**: Record audio directly from the browser/mobile and transcribe it using **ElevenLabs Scribe** (`scribe_v1` model).
- **Playback**: Instant audio playback for generated speech.

### 📱 Multi-Platform Experience
- **Web Dashboard**: React-based interface for managing calls, viewing history, and using the Voice Generator.
- **Mobile App**: React Native (Expo) companion app.
    - **Floating Action Button (FAB)**: Integrated "Mic" button in the footer that seamlessly links to the web-based Voice Generator platform.
    - **Glassmorphism UI**: Modern, sleek design with blur effects.

### 🔐 Architecture & Security
- **Secure Authentication**: Robust user registration and login system with password hashing (`bcryptjs`) and JWT-ready architecture.
- **Call History**: Persistent tracking of all call activities stored in Raindrop KV Cache.
- **Cloud Native**: Fully serverless architecture powered by Raindrop.

---

## 🛠️ Technology Stack

| Component | Technology | Description |
|-----------|------------|-------------|
| **Backend** | [Raindrop Framework](https://github.com/liquidmetal-ai/raindrop) | Serverless Hono.js API & Workers |
| **Frontend** | React, Vite, TailwindCSS | Modern Web Dashboard |
| **Mobile** | React Native, Expo | iOS/Android Companion App |
| **AI (TTS)** | ElevenLabs | Text-to-Speech Generation |
| **AI (STT)** | ElevenLabs Scribe | High-accuracy Transcription |
| **Database** | Raindrop KV Cache | Scalable Key-Value Store |

---

## 🚀 Getting Started

### Prerequisites
- **Node.js**: v18 or higher
- **npm**: v9 or higher
- **Raindrop CLI**: Included in project dependencies

### 1️⃣ Installation
Clone the repository and install dependencies for all workspace components:

```bash
# Install root dependencies (Backend)
npm install

# Install Frontend dependencies
cd frontend && npm install && cd ..

# Install Mobile App dependencies
cd mobile-app && npm install && cd ..
```

### 2️⃣ Configuration (Crucial)
To enable the AI capabilities, you need to configure your secrets in the Raindrop environment.

**ElevenLabs Setup:**
> [!IMPORTANT]
> A **Paid Subscription** (e.g., Creator/Starter) is required for ElevenLabs to work from cloud environments. Free Tier accounts will be blocked with a 401 error.

Set your API key using the Raindrop CLI:
```bash
./node_modules/.bin/raindrop build env set ELEVENLABS_API_KEY "your-api-key-here"
```

### 3️⃣ Running the Application
Start the entire stack (Backend + Frontend + Mobile) with a single command:

```bash
npm run dev
```

This will concurrently launch:
*   **Backend API**: Deployed to Raindrop Sandbox.
*   **Web Frontend**: [http://localhost:5173](http://localhost:5173)
*   **Mobile Web Preview**: [http://localhost:8081](http://localhost:8081)

> [!NOTE]
> If you make changes to the backend code (e.g., `src/api/calls.ts`), you must **restart** the `npm run dev` process to redeploy the changes.

---

## 🧪 Testing & Verification

### Verify Backend Health
Check if the API is running:
```bash
curl https://<your-service-url>/health
```

### Test Voice Generation (API)
You can manually test the Text-to-Speech webhook:

```bash
curl -X POST https://<your-service-url>/api/calls/webhooks/voice \
  -H "Content-Type: application/json" \
  -d '{"text": "Hello, this is a test.", "voice_id": "pNInz6obpgDQGcFmaJgB"}'
```

### Test Transcription (API)
You can upload an audio file to test Speech-to-Text:

```bash
curl -X POST https://<your-service-url>/api/calls/transcribe \
  -F "file=@/path/to/audio.webm"
```

---

## ⚠️ Troubleshooting

### ElevenLabs 401 Unauthorized
**Error:** `Unusual activity detected. Free Tier usage disabled.`
**Cause:** ElevenLabs strict security policy blocks API requests from cloud/data-center IP addresses for Free Tier accounts.
**Fix:** Upgrade your ElevenLabs account to a **Paid Subscription** (e.g., Creator).

### "API Stuck Reading Old Text"
**Cause:** The backend code might be stale if `npm run dev` was running while changes were made.
**Fix:** Stop the server (Ctrl+C) and run `npm run dev` again to trigger a fresh deployment.

---

## 📂 Project Structure

```
raindrop-app/
├── src/
│   ├── api/          # Backend Logic (Hono.js)
│   │   ├── auth.ts   # User Registration/Login
│   │   ├── calls.ts  # Call Logic, TTS & STT Integration
│   │   └── db.ts     # Database Helpers
│   └── ...
├── frontend/         # Web Application (React/Vite)
│   ├── src/pages/    # Next-gen UI Pages (VoiceGenerator, Dashboard, etc.)
│   └── ...
├── mobile-app/       # Mobile Application (Expo)
│   ├── src/components/ # Shared Mobile Components (Link to Web FAB)
│   └── ...
├── raindrop.manifest # Infrastructure Config
└── package.json      # Project Scripts
```
