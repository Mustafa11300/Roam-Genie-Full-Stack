<div align="center">

<img src="https://img.shields.io/badge/RoamGenie-AI%20Travel%20Platform-0b2d6e?style=for-the-badge&logoColor=white" alt="RoamGenie"/>

# 🌍 RoamGenie

### *Your AI-Powered Travel Orchestration Platform*

**Intelligent travel automation powered by AI agents, real-time monitoring, and seamless communication workflows**

[![Node.js](https://img.shields.io/badge/Node.js-18%2B-339933?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org)
[![React](https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react&logoColor=black)](https://reactjs.org)
[![Vite](https://img.shields.io/badge/Vite-7.x-646CFF?style=flat-square&logo=vite&logoColor=white)](https://vitejs.dev)
[![Gemini](https://img.shields.io/badge/Google-Gemini%20AI-4285F4?style=flat-square&logo=google&logoColor=white)](https://ai.google.dev)
[![Twilio](https://img.shields.io/badge/Twilio-WhatsApp%20%26%20IVR-F22F46?style=flat-square&logo=twilio&logoColor=white)](https://twilio.com)
[![n8n](https://img.shields.io/badge/n8n-Workflow%20Automation-EA4B71?style=flat-square&logo=n8n&logoColor=white)](https://n8n.io)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

<br/>

[Features](#-features) · [Architecture](#-architecture) · [Getting Started](#-getting-started) · [API Reference](#-api-reference) · [n8n Workflows](#-n8n-workflows) · [Contributing](#-contributing)

---

</div>

## 🧭 Overview

**RoamGenie** is a full-stack AI travel agent platform that orchestrates complex travel workflows through intelligent AI agents, real-time data processing, and multi-channel communication. Built for developers who want to automate travel operations at scale — from booking discovery to emergency alerts — RoamGenie connects every piece of your travel stack into one cohesive, intelligent system.

> Built with a Node.js backend, React frontend, Google Gemini AI, Twilio communications, SerpApi data retrieval, and n8n workflow automation.

---

## ✨ Features

### 🤖 1. AI Travel Companion Agent (ATCA)
The core intelligence layer of RoamGenie. Provides real-time itinerary updates, booking tracking, and traveler support across WhatsApp, web, and mobile interfaces.

- Real-time itinerary management and status updates
- Booking tracking with proactive status notifications
- Emergency information routing and escalation
- Offline fallback messaging via WhatsApp when connectivity is lost
- Personalized travel recommendations based on traveler profile

---

### 📞 2. AI Inquiry Call Agent (AICA)
A multilingual IVR voice bot that handles inbound traveler calls without human intervention.

- Automated booking lookups and confirmations
- Refund request processing and status updates
- Intelligent escalation to human agents when needed
- Supports multiple languages for international travelers
- Powered by Twilio Programmable Voice

---

### 🔍 3. Search & Data Retrieval
Real-time travel data acquisition using SerpApi — the backbone of RoamGenie's flight and accommodation search.

- Live flight search with pricing, airlines, duration, and layover details
- Hotel and resort discovery with ratings, images, amenities, and proximity data
- Activity and experience search for destination enrichment
- Structured data extraction ready for AI processing and email generation

---

### 📄 4. Text & Document Analysis (OCR)
Intelligent document processing that reads and extracts structured information from uploaded images and files.

- Passport scan and data extraction
- Booking confirmation document parsing
- ID and travel document recognition
- Powered by Google Gemini Vision and native OCR service

---

### 💬 5. Communication Workflows
Multi-channel notification and interaction system using Twilio.

- WhatsApp message delivery for itinerary updates and alerts
- IVR call flows for voice-based traveler support
- Emergency broadcast alerts to traveler devices
- Automated notification triggers based on booking events

---

### ⚙️ 6. Orchestration Hub
The central coordination layer that manages data acquisition, processing pipelines, and alert routing.

- Unified API gateway for all travel data sources
- Event-driven alert system for booking changes
- Background job scheduling for proactive monitoring
- Logging and observability via Winston

---

### 🌐 7. Travel & Customer Support
End-to-end customer support infrastructure built for global travel operations.

- Multilingual support across IVR and WhatsApp channels
- Structured knowledge base for common traveler queries
- Escalation routing from AI agent to human support
- Full conversation history and context preservation

---

### 🛂 8. Passport Scanner
Upload a passport photo and instantly discover visa-free travel destinations.

- Extracts nationality, expiry date, and document number via OCR
- Cross-references passport country against global visa requirement databases
- Returns a list of visa-free and visa-on-arrival destinations
- Flags upcoming passport expiry risks before booking

---

### 🚨 9. Emergency & Offline Support
Proactive emergency management and offline resilience.

- Flight cancellation alert simulation and real handling
- Offline fallback messages delivered via WhatsApp when app is unreachable
- Emergency contact routing and escalation workflows
- Real-time disruption notifications with rebooking guidance

---

### 📋 10. CRM Integration (Vendasta)
Captures traveler lead data and pushes it directly into your CRM system.

- Contact form submissions saved to Vendasta CRM automatically
- Traveler profile enrichment with destination and booking preferences
- Lead tracking from first inquiry to completed booking
- API-based integration — swap Vendasta for any CRM with minimal changes

---

### 🧬 11. AI Trip DNA Scanner *(New)*
The zero-effort itinerary builder. Forward any booking confirmation — email, PDF, screenshot — and RoamGenie extracts every detail automatically.

- Parses flight confirmations, hotel vouchers, car rentals, and tour packages
- Extracts PNR, seat, baggage allowance, terminal, check-in/out times, and more
- Cross-references passport nationality to flag transit visa requirements
- Sends a structured WhatsApp confirmation summary automatically
- Supports text paste, PDF upload, and image upload

**Supported input formats:** Plain text · PDF · JPG · PNG · WebP

```
User forwards booking email
        ↓
Gemini Vision parses all fields
        ↓
Visa check against passport country
        ↓
Structured itinerary JSON returned
        ↓
WhatsApp confirmation sent automatically
```

---

### 🚨 12. Live Trip War Room *(New)*
Real-time disruption intelligence. RoamGenie monitors your active flights 24/7 and alerts you before problems become crises.

- Flight status polling every 30 minutes via AviationStack API
- Delay detection with automatic connection viability calculation
- Travel advisory monitoring via SerpApi news search
- Gemini-powered plain-English alert summaries
- WhatsApp push alerts for delays, cancellations, gate changes, and advisories
- User-configurable monitoring per trip with manual "Check Now" override

**Alert severity levels:**

| Level | Trigger | Action |
|-------|---------|--------|
| 🔵 Info | Gate change, minor update | Notification only |
| 🟡 Warning | Delay > 30min, tight connection | Notification + advisory |
| 🔴 Critical | Cancellation, missed connection | Immediate alert + alternatives |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        ROAMGENIE PLATFORM                       │
├───────────────────────┬─────────────────────────────────────────┤
│      FRONTEND         │              BACKEND                    │
│   React + Vite        │           Node.js + Express             │
│                       │                                         │
│  ┌─────────────────┐  │  ┌──────────┐  ┌──────────────────────┐│
│  │   Pages         │  │  │  Routes  │  │      Services        ││
│  │  - Itinerary    │◄─┼─►│ /travel  │  │  flightService.js    ││
│  │  - Passport     │  │  │ /passport│  │  geminiService.js    ││
│  │  - Dashboard    │  │  │ /ivr     │  │  ocrService.js       ││
│  │  - War Room     │  │  │ /contact │  │  passportService.js  ││
│  └─────────────────┘  │  │ /emergency  │  twilioService.js    ││
│  ┌─────────────────┐  │  │ /trip-dna│  │  tripDnaService.js   ││
│  │  Components     │  │  │ /war-room│  │  warRoomService.js   ││
│  │  TripDnaScanner │  │  └──────────┘  │  pollingService.js   ││
│  │  WarRoomPanel   │  │                └──────────────────────┘│
│  └─────────────────┘  │                                         │
│  ┌─────────────────┐  │  ┌──────────────────────────────────┐  │
│  │  Hooks          │  │  │         External APIs            │  │
│  │  useWarRoom.js  │  │  │  Google Gemini · SerpApi         │  │
│  └─────────────────┘  │  │  AviationStack · Twilio          │  │
│  ┌─────────────────┐  │  │  Vendasta CRM                    │  │
│  │  API Layer      │  │  └──────────────────────────────────┘  │
│  │  tripDnaApi.js  │  │                                         │
│  │  warRoomApi.js  │  │  ┌──────────────────────────────────┐  │
│  │  flightApi.js   │  │  │         n8n Workflows            │  │
│  │  itineraryApi.js│  │  │  Flight Search → Email           │  │
│  └─────────────────┘  │  │  Booking → CRM → WhatsApp        │  │
└───────────────────────┴──┴──────────────────────────────────────┘
```

---

## 🗂️ Project Structure

```
📦 RoamGenie
├── 📁 Backend_Roam_genie/
│   ├── 📁 logs/                        # Winston log output
│   ├── 📁 src/
│   │   ├── 📁 routes/
│   │   │   ├── travel.js               # Flight & travel search routes
│   │   │   ├── passport.js             # Passport scan routes
│   │   │   ├── ivr.js                  # Twilio IVR routes
│   │   │   ├── contact.js              # CRM contact routes
│   │   │   ├── emergency.js            # Emergency alert routes
│   │   │   ├── tripDnaRoutes.js        # 🧬 Trip DNA Scanner routes
│   │   │   └── warRoomRoutes.js        # 🚨 War Room routes
│   │   ├── 📁 services/
│   │   │   ├── flightService.js        # AviationStack / SerpApi flight data
│   │   │   ├── geminiService.js        # Google Gemini AI integration
│   │   │   ├── ocrService.js           # OCR document processing
│   │   │   ├── passportService.js      # Passport scan & visa logic
│   │   │   ├── twilioService.js        # WhatsApp & IVR communications
│   │   │   ├── tripDnaService.js       # 🧬 Booking parsing engine
│   │   │   ├── warRoomService.js       # 🚨 Flight monitoring engine
│   │   │   └── pollingService.js       # 🚨 Background scheduler
│   │   ├── 📁 utils/
│   │   │   └── logger.js               # Winston logger
│   │   └── server.js                   # Express app entry point
│   ├── .env
│   ├── eng.traineddata                 # Tesseract OCR language data
│   └── package.json
│
└── 📁 ROAM-GENIE/                      # React Frontend
    ├── 📁 src/
    │   ├── 📁 api/
    │   │   ├── contactApi.js
    │   │   ├── flightApi.js
    │   │   ├── itineraryApi.js
    │   │   ├── ivrApi.js
    │   │   ├── passportApi.js
    │   │   ├── tripDnaApi.js           # 🧬 Trip DNA API calls
    │   │   └── warRoomApi.js           # 🚨 War Room API calls
    │   ├── 📁 components/
    │   │   ├── TripDnaScanner.jsx      # 🧬 Booking import UI
    │   │   └── WarRoomPanel.jsx        # 🚨 Live monitoring UI
    │   ├── 📁 context/
    │   ├── 📁 hooks/
    │   │   └── useWarRoom.js           # 🚨 War Room polling hook
    │   ├── 📁 pages/
    │   ├── 📁 utils/
    │   ├── App.jsx
    │   └── main.jsx
    ├── .env
    └── package.json
```

---

## 🚀 Getting Started

### Prerequisites

| Requirement | Version |
|-------------|---------|
| Node.js | 18+ |
| npm | 9+ |
| Twilio Account | Active |
| Google Gemini API Key | Active |
| SerpApi Key | Active |
| AviationStack API Key | Free tier works |
| n8n | Self-hosted or cloud |

---

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/roamgenie.git
cd roamgenie
```

---

### 2. Backend Setup

```bash
cd Backend_Roam_genie
npm install
```

Create your `.env` file:

```env
# ── Server ──────────────────────────────────────────
PORT=3000

# ── Google Gemini AI ─────────────────────────────────
GEMINI_API_KEY=your_gemini_api_key_here

# ── Twilio ───────────────────────────────────────────
TWILIO_ACCOUNT_SID=your_twilio_account_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_PHONE_NUMBER=your_twilio_phone_number
TWILIO_WHATSAPP_FROM=whatsapp:+14155238886

# ── SerpApi ──────────────────────────────────────────
SERPAPI_KEY=your_serpapi_key_here

# ── AviationStack (War Room) ─────────────────────────
AVIATIONSTACK_API_KEY=your_aviationstack_key_here

# ── CRM ──────────────────────────────────────────────
VENDASTA_API_KEY=your_vendasta_key_here

# ── War Room Scheduler ───────────────────────────────
WAR_ROOM_POLL_INTERVAL=30
```

Start the backend:

```bash
# Development (with nodemon auto-restart)
npm run dev

# Production
npm start
```

Backend runs at → `http://localhost:3000`

---

### 3. Frontend Setup

```bash
cd ROAM-GENIE
npm install
```

Create your `.env` file:

```env
VITE_API_BASE_URL=http://localhost:3000
```

Start the frontend:

```bash
npm run dev
```

Frontend runs at → `http://localhost:5173`

---

### 4. Verify Everything Works

```bash
# Health check
curl http://localhost:3000/health

# Expected response:
# { "status": "ok", "service": "RoamGenie Backend", "timestamp": "..." }
```

---

## 📡 API Reference

### Core Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/health` | Server health check |
| `POST` | `/api/travel/search` | Search flights and travel options |
| `POST` | `/api/passport/scan` | Scan passport and get visa-free destinations |
| `POST` | `/api/ivr/incoming` | Handle inbound IVR calls |
| `POST` | `/api/contact/save` | Save contact to CRM |
| `POST` | `/api/emergency/alert` | Trigger emergency alert |

### 🧬 Trip DNA Scanner

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/trip-dna/scan-text` | Scan raw booking confirmation text |
| `POST` | `/api/trip-dna/scan-file` | Scan base64 PDF or image file |

**Request — Scan Text:**
```json
POST /api/trip-dna/scan-text
{
  "text": "Your booking is confirmed. Flight EK512...",
  "passportCountry": "IN",
  "whatsappNumber": "+911234567890"
}
```

**Request — Scan File:**
```json
POST /api/trip-dna/scan-file
{
  "base64Data": "JVBERi0xLjQK...",
  "mimeType": "application/pdf",
  "passportCountry": "IN",
  "whatsappNumber": "+911234567890"
}
```

**Response:**
```json
{
  "success": true,
  "extracted": {
    "bookingType": "flight",
    "flights": [{
      "flightNumber": "EK512",
      "airline": "Emirates",
      "departure": { "city": "Dubai", "airport": "DXB", "date": "2025-06-12", "time": "14:30" },
      "arrival": { "city": "London", "airport": "LHR", "date": "2025-06-12", "time": "18:45" },
      "pnr": "ABC123",
      "seat": "24A",
      "baggage": "30kg"
    }],
    "hotels": [],
    "passenger": { "name": "John Doe" }
  },
  "visaWarnings": [{ "transitCity": "London", "transitCountry": "GB", "visaRequired": true }],
  "hasVisaWarning": true,
  "scannedAt": "2025-06-01T10:30:00Z"
}
```

---

### 🚨 Live Trip War Room

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/war-room/subscribe` | Register trip for monitoring |
| `GET` | `/api/war-room/status/:tripId` | Get current alerts and status |
| `POST` | `/api/war-room/trigger-check` | Manually trigger immediate check |
| `DELETE` | `/api/war-room/unsubscribe/:tripId` | Stop monitoring a trip |
| `GET` | `/api/war-room/polling-status` | Check scheduler health |

**Request — Subscribe:**
```json
POST /api/war-room/subscribe
{
  "tripId": "trip_abc123",
  "userId": "user_456",
  "whatsappNumber": "+911234567890",
  "destination": "London",
  "flights": [
    { "flightNumber": "EK512", "date": "2025-06-12", "layoverMinutes": 90 },
    { "flightNumber": "BA201", "date": "2025-06-12" }
  ]
}
```

**Response — Status:**
```json
{
  "success": true,
  "tripId": "trip_abc123",
  "status": "monitoring",
  "overallSeverity": "warning",
  "lastChecked": "2025-06-12T08:00:00Z",
  "alerts": [{
    "type": "delay",
    "severity": "warning",
    "flightNumber": "EK512",
    "delayMinutes": 45,
    "message": "Flight EK512 delayed by 45 minutes",
    "connectionViability": {
      "isViable": true,
      "remainingMinutes": 45,
      "riskLevel": "tight"
    }
  }]
}
```

---

## 🔄 n8n Workflows

RoamGenie uses n8n as its workflow automation backbone. Here's what's automated:

### Flight Search → HTML Email Workflow

The primary travel discovery workflow that orchestrates search, aggregation, and AI email generation.

```
Webhook Trigger
      ↓
Set Fields (origin, destination, dates)
      ↓
┌─────────────────┬──────────────┐
│  Flight Search  │   Resorts    │  Activities
│  (SerpApi)      │   (SerpApi)  │  (SerpApi)
└────────┬────────┴──────┬───────┘
         │               │
         └───────┬───────┘
                 ↓
         AI Email Generator
         (Gemini / OpenAI)
                 ↓
         Send Email (Gmail/SMTP)
```

**User Message Template** — passes structured data to the AI:

```
# Flights from {origin} to {destination} on {departure_date} to {return_date}

1) {airline}, departing at {time}, duration: {duration} minutes
   From: {departure_airport} ({code}) → To: {arrival_airport} ({code})
   Flight Number: {flight_number} | Class: {travel_class}
   Features: {extensions}
   Price: ${price}, {type}

# Resorts
1) {name} | Link: {link}
   Rating: {overall_rating} ({reviews} reviews)
   Rate: {rate_per_night} / night | Total: {total_rate}
   Nearby: {nearby_places}
   Amenities: {amenities}

# Activities
1) {title} | Link: {url}
   {description}
```

**System Message Highlights:**
- Outputs two parameters: `subject` (plain text) and `emailBody` (complete HTML)
- Inline CSS only — compatible with Gmail, Outlook, Apple Mail
- Navy `#0b2d6e` brand colors throughout
- Resort images rendered as responsive HTML `<img>` tags
- All resort and activity names rendered as clickable links
- Under 1000 words of body copy

---

### Other n8n Workflow Ideas

| Workflow | Trigger | Actions |
|----------|---------|---------|
| **Booking Confirmation** | New booking webhook | Save to CRM → Send WhatsApp → Log to sheet |
| **War Room Alert** | War Room API webhook | Assess severity → Notify traveler → Log alert |
| **Passport Expiry Check** | Scheduled (weekly) | Check expiry → Alert traveler if <6 months |
| **Emergency Broadcast** | Emergency route trigger | WhatsApp blast → IVR outbound → Email |

---

## 🧰 Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Frontend** | React 18 + Vite 7 | UI framework |
| **Styling** | Tailwind CSS | Component styling |
| **Backend** | Node.js + Express | API server |
| **AI** | Google Gemini 1.5 Flash | Document parsing, summaries, email generation |
| **OCR** | ocrService + Gemini Vision | Document text extraction |
| **Communications** | Twilio | WhatsApp, IVR, SMS |
| **Flight Data** | SerpApi + AviationStack | Live flight search and status |
| **Hotel Data** | SerpApi Hotels | Resort search and pricing |
| **Automation** | n8n | Workflow orchestration |
| **CRM** | Vendasta | Contact and lead management |
| **Security** | Helmet + express-rate-limit | API protection |
| **Logging** | Winston + Morgan | Structured logging |

---

## 🔐 Security

- **Helmet.js** — sets secure HTTP headers on all responses
- **CORS** — restricted to configured allowed origins only
- **Rate Limiting** — 100 requests per 15 minutes per IP
- **Input Validation** — all API endpoints validate required fields before processing
- **File Size Limits** — base64 file uploads capped at 15MB
- **Environment Variables** — all secrets stored in `.env`, never in source code

---

## 📊 Logging

RoamGenie uses **Winston** for structured server-side logging and **Morgan** for HTTP request logging.

Log files are written to the `logs/` directory:

```
logs/
├── combined.log    # All log levels
└── error.log       # Error level only
```

Each service prefixes its logs for easy filtering:

```
[TripDNA]  Starting text scan
[WarRoom]  Running check { tripId: 'trip_abc123' }
[Polling]  Cycle complete { checked: 3, alertsFound: 1, errors: 0 }
```

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/your-feature-name`
3. Commit your changes: `git commit -m 'feat: add your feature'`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a Pull Request

Please follow the existing service/route file naming conventions and add appropriate Winston log entries to any new service.

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Built with ❤️ for travelers everywhere**

*RoamGenie — Your journey, our passion.*

</div>