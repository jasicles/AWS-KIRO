# PantryPal — AI-Powered Kitchen Assistant

> Snap a photo of your fridge. Get personalized recipes. Reduce food waste. Cook like a pro.

PantryPal is an intelligent food assistant that uses AI to extract ingredients from photos, manage your pantry, generate personalized recipes based on your mood, health needs, and cuisine preferences, and help you reduce food waste — all powered by a serverless AWS architecture.

---

## Key Features

### Smart Image Upload
- Drag & drop fridge/receipt photos
- AI-powered ingredient extraction with live processing pipeline
- Visual transformation animation: raw image → structured pantry data

### Intelligent Pantry Dashboard
- Grid of ingredient cards with freshness tracking (Fresh / Use Soon)
- Quantity controls and stock amounts
- Search & filter by category
- AI Insights that speak in natural language
- Food Waste Score with impact analytics

### AI Recipe Generator
- **Mood-based**: Creamy, Spicy, Healthy, Comfort, Quick
- **Cuisine-based**: Chinese, Japanese, Korean, Thai, Indian, Italian, Mexican + more
- **Health-aware**: Diabetes, High Cholesterol, Blood Pressure, Gluten-Free, Lactose Intolerant
- **Diet goals**: High Protein, Low Fat, High Fibre, Low Carb, Keto, Vegan, Vegetarian
- Specific ingredient quantities and protein info per recipe
- Expiry-priority logic (uses ingredients closest to expiring first)
- Save recipes for later

### Cook Mode
- Full-screen immersive cooking interface
- Step-by-step instructions with exact measurements
- Ingredient checklist with quantities
- Real-time progress indicator and timer
- Auto-updates pantry when cooking completes
- Share your dish photo to your Pantry Circle

### Smart Shopping List
- Auto-generated from missing recipe ingredients
- "Where to Buy" links to Singapore stores (FairPrice, Cold Storage, Giant, RedMart, Sheng Siong, Redman)
- Checkboxes with progress bar

### AI Chat Assistant
- Pantry-aware conversational AI
- Ask "What can I cook tonight?" or "What's expiring soon?"
- Natural, friendly responses with personality

### Global Kitchen Challenge
- Daily rotating cuisine themes (Rome → Tokyo → Mexico City...)
- Automatic point scoring: +10 cooking, +5 theme match, +3 expiring items
- Level system with streak tracking

### Pantry Circles (Social)
- Create/join circles with friends via invite code
- Aggregated food waste reduction stats
- Weekly rankings with medals
- Shared dishes gallery & group cooking "Moments"
- Friendly comparisons (achievements, not harsh rankings)

### Kitchen Story Mode
- Instagram Stories-style narrative timeline
- Visualizes your pantry journey with animated cards
- AI narration and meal recommendations

### Autopilot Mode
- Proactive AI insights without user prompts
- Expiry warnings, meal suggestions, shopping recommendations
- Simulated AWS EventBridge scheduled triggers

### Live Architecture View
- Visual AWS pipeline diagram
- Animated simulation: S3 → Lambda → Bedrock → DynamoDB → Frontend
- Clickable "Simulate Request" to watch data flow

### AI Explainability
- "Why?" button on every AI decision
- Shows reasoning, confidence score, and data source
- Builds trust and transparency

---

## Architecture

```
Client (React) → API Gateway (Express) → S3 (Storage)
                                              ↓
                                        EventBridge
                                              ↓
                    ┌─────────────────────────────────────────┐
                    │         Lambda AI Agents (×4)            │
                    │  • Ingredient Detection (Bedrock Vision) │
                    │  • Freshness Inference                   │
                    │  • Recipe Generation                     │
                    │  • Insight Generation                    │
                    └─────────────────────────────────────────┘
                                              ↓
                                        DynamoDB (State)
                                              ↓
                                     Frontend (Polling)
```

---

## Built With

| Layer | Technology |
|-------|-----------|
| Frontend | React 18, Vite, CSS3 (custom animations) |
| Backend | Node.js, Express.js, ES Modules |
| AI | Amazon Bedrock (Claude 3 Sonnet) |
| Storage | Amazon S3 (simulated locally) |
| Compute | AWS Lambda (4 AI agents, simulated) |
| Database | Amazon DynamoDB (simulated) |
| Events | Amazon EventBridge (simulated) |
| Font | Inter (Google Fonts) |

---

## Getting Started

### Prerequisites
- Node.js 18+ installed

### Installation
```bash
git clone https://github.com/YOUR_USERNAME/pantrypal.git
cd pantrypal
npm install
```

### Run Development Servers
```bash
# Terminal 1 — Backend (port 3001)
npm run dev:backend

# Terminal 2 — Frontend (port 3000)
npm run dev:frontend
```

Open `http://localhost:3000` in your browser.

> **Note:** The app runs fully in mock mode without AWS credentials. All AI features work with realistic simulated data.

---

## Project Structure

```
pantrypal/
├── frontend/                    React app
│   └── src/
│       ├── components/          UI components (15+)
│       ├── services/            API client + store links
│       └── styles/              Design system (1200+ lines CSS)
├── backend/                     Node.js server
│   └── src/
│       ├── ai/                  Bedrock abstraction + 4 Lambda agents
│       ├── api/                 REST route handlers
│       └── services/            Business logic + simulated AWS services
├── package.json                 Workspaces root
└── README.md
```

---

## Singapore Store Integration

Shopping list items link directly to search pages of local grocery stores:
- FairPrice — everyday groceries
- Giant — budget essentials
- Sheng Siong — Asian ingredients
- RedMart (Lazada) — online delivery
- Cold Storage — premium imported goods
- Redman — specialty baking supplies

---

## Demo Highlights

1. **Cinematic intro** — Apple-style product reveal on first load
2. **AI Thinking Sequence** — 5-step animated processing pipeline
3. **Transformation animation** — raw image → structured pantry (split-screen)
4. **Cook Mode** — full-screen guided cooking with timer
5. **Architecture visualization** — live animated AWS diagram
6. **60+ animations** — everything feels fluid and premium

---

## Team

Built for AWS Kiro Buildfest 2026 Hackathon Singapore

---

## 📄 License

MIT
