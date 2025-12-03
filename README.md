# HoldMySpot

**HoldMySpot** is an advanced AI-powered platform designed to reclaim your time. By leveraging agentic AI, we navigate complex phone trees, wait on hold, and negotiate with service providers on your behalf.

## 🚀 Mission

Our mission is simple: **Never Wait on Hold Again.**
We empower users by handling the frustration of day-to-day bureaucracy—dealing with utility companies, airlines, healthcare providers, and more—so you can focus on what truly matters.

## 🛠 Technology Stack

HoldMySpot is built with a modern, scalable, and secure stack, ensuring a seamless experience across web and mobile.

### Frontend (Web)
- **Framework**: React (Vite)
- **Styling**: Tailwind CSS (Custom "Elite" Design System)
- **Icons**: Lucide React
- **Routing**: React Router
- **State Management**: React Context API

### Mobile App (Web & Native)
- **Framework**: React Native (Expo)
- **Styling**: NativeWind (Tailwind CSS for Mobile)
- **Navigation**: React Navigation (Stack & Bottom Tabs)
- **Platform**: iOS, Android, and Web (PWA)

### Backend
- **Runtime**: Node.js
- **Framework**: Express.js
- **Language**: TypeScript
- **Security**: 
  - **bcryptjs**: Secure password hashing.
  - **Multi-Layer Encryption**: Custom double-layer AES-256 encryption for sensitive data.
- **API**: RESTful architecture

### AI & Infrastructure
- **Voice Synthesis**: ElevenLabs (Ultra-realistic Text-to-Speech)
- **Telephony**: Vultr (High-performance Call Dispatching)
- **Storage**: Raindrop SmartMemory (Secure Verification Vault)

## ✨ Features

1.  **Instant Dispatch**: Launch an AI agent to handle calls immediately from the Web or Mobile App.
2.  **Real-Time Dashboard**: Track the status of your calls (Queued, On Hold, Connected, Completed).
3.  **Secure Verification Vault**: Store sensitive information (DOB, SSN, Mother's Maiden Name) securely. This data is encrypted with multiple layers of protection and only decrypted when the agent needs it to verify your identity.
4.  **Cross-Platform Experience**: 
    - **Web App**: Full-featured desktop experience.
    - **Mobile App**: Optimized for touch, with a dedicated "Web App" mode for browser access.
5.  **Bank-Grade Security**: 
    - All passwords are hashed.
    - Personal data is encrypted at rest using a multi-layer encryption strategy.

## 📦 Installation & Setup

### Prerequisites
- Node.js (v18+)
- npm

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/hold-my-spot.git
cd hold-my-spot
```

### 2. Install Dependencies
We use a unified build system. You can install dependencies for all components from the root:

```bash
# Install root dependencies
npm install

# Install Frontend dependencies
cd frontend && npm install

# Install Backend dependencies
cd ../backend && npm install

# Install Mobile App dependencies
cd ../mobile-app && npm install
```

### 3. Environment Variables
Create a `.env` file in the `backend` directory:

```env
PORT=3000
ENCRYPTION_KEY_1=your_32_char_key_1
ENCRYPTION_KEY_2=your_32_char_key_2
```

### 4. Run the Application
You can run the entire platform (Backend, Frontend, and Mobile Web App) concurrently from the root directory:

```bash
# From the root directory
npm run all
```

This command will start:
- **Backend API**: http://localhost:3000
- **Frontend Web**: http://localhost:5173
- **Mobile Web App**: http://localhost:8081

## 📱 Mobile App Usage

The mobile application is designed to run seamlessly in the browser or on a device.
- **Access**: Click "Web App" in the main website's navigation bar.
- **Features**:
    - **Hold My Spot**: Dispatch calls directly.
    - **History**: View your call logs.
    - **Profile**: Manage your account settings.
    - **Guest Mode**: Try the app without creating an account immediately.

## 🔒 Security Architecture

Security is paramount at HoldMySpot.

- **Authentication**: Secure session management and token-based authentication.
- **Data Protection**: 
  - **At Rest**: Sensitive data is encrypted using a double-layer AES-256-CBC algorithm. Each layer uses a distinct 256-bit key.
  - **In Transit**: All data transmission occurs over HTTPS (in production).
- **Privacy**: We only store what is absolutely necessary for the agent to perform its task.

---

*Built with ❤️ for the AI Championship.*
