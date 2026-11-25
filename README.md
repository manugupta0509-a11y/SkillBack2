# SkillBack — Restart Your Career

AI-powered career comeback platform for experienced professionals returning after career breaks.

## Tech Stack

- **Frontend**: React.js + Vite + Tailwind CSS + Recharts
- **Backend**: Node.js + Express.js + REST APIs
- **Database**: MongoDB (with full demo mode fallback)

## Quick Start (Demo Mode — no MongoDB required)

### 1. Backend

```bash
cd backend
cp .env.example .env
npm install
npm run dev
```

The backend starts on `http://localhost:5000` in demo mode (in-memory data).

### 2. Frontend

```bash
cd frontend
npm install
npm run dev
```

The frontend starts on `http://localhost:5173` and proxies API calls to the backend.

### 3. Open the app

Visit `http://localhost:5173` in your browser.

## User Journey

1. **Landing Page** — Learn about SkillBack and create an account
2. **Register / Login** — Create your account
3. **Profile** — Add work experience, education, skills, career break details
4. **Skills Discovery** — AI analyzes your skills, hidden strengths, and transferable abilities
5. **Market Intelligence** — Compare your skills against market demand, identify gaps
6. **Learning Pathway** — Personalized learning roadmap with curated resources
7. **Inclusive Job Matching** — Match with jobs without penalizing career breaks
8. **Bias Audit** — Automated fairness check across 8 criteria
9. **ReverseMentor** — Two-way mentoring between experienced professionals and digital natives
10. **Dashboard** — Overview with charts, progress tracking, and quick actions

## 5 AI Agents

Each agent supports three modes: AI API integration, rule-based fallback, and demo mode.

| Agent | Purpose |
|-------|---------|
| Skills Discovery | Analyzes work history to identify technical, soft, and transferable skills |
| Market Intelligence | Compares skills against market demands, identifies gaps and trends |
| Learning Pathway | Generates personalized learning roadmap with curated resources |
| Inclusive Matching | Matches jobs without penalizing career breaks, transparent scoring |
| Bias Audit | Audits matching results for fairness across 8 criteria |

## AI API Configuration (Optional)

To use real AI instead of rule-based fallback, set these in `backend/.env`:

```
AI_API_KEY=your-api-key
AI_API_BASE_URL=https://api.example.com/v1
AI_MODEL=your-model-name
```

## MongoDB (Optional)

To use persistent storage instead of demo mode:

```
DEMO_MODE=false
MONGODB_URI=mongodb://localhost:27017/skillback
```

## SAP Integration Readiness

SAP integration is stubbed out in `backend/src/services/sapIntegration.js`. The placeholder is ready for real SAP API endpoints when available. No invented SAP APIs are included.

## API Endpoints

### Auth
- `POST /api/auth/register` — Register new user
- `POST /api/auth/login` — Login
- `GET /api/auth/me` — Get current user

### Profile
- `GET /api/profile` — Get profile
- `PUT /api/profile` — Update profile

### Agents
- `POST /api/agents/skills` — Run Skills Discovery
- `POST /api/agents/market` — Run Market Intelligence
- `POST /api/agents/learning` — Run Learning Pathway
- `POST /api/agents/matching` — Run Inclusive Matching
- `POST /api/agents/bias-audit` — Run Bias Audit
- `POST /api/agents/orchestrate` — Run all 5 agents in sequence

### Jobs
- `GET /api/jobs` — List jobs (supports filters)

### Mentors
- `GET /api/mentors` — List mentors
- `POST /api/mentors/request` — Send mentorship request
- `GET /api/mentors/requests` — Get my requests
- `POST /api/mentors/requests/:id/message` — Send message

### Learning
- `GET /api/learning/progress` — Get learning progress
- `PUT /api/learning/progress/:moduleIndex` — Update module progress

## Project Structure

```
skillback-v2/
├── backend/
│   ├── src/
│   │   ├── agents/          # 5 AI agents + orchestrator
│   │   ├── config/          # Database connection
│   │   ├── controllers/     # Route handlers
│   │   ├── middleware/       # Auth middleware
│   │   ├── models/          # Mongoose models
│   │   ├── routes/          # Express routes
│   │   ├── services/        # SAP integration stub
│   │   ├── utils/           # JWT token generation
│   │   └── server.js        # Express app entry
│   ├── .env.example
│   └── package.json
├── frontend/
│   ├── src/
│   │   ├── components/      # Layout, landing, dashboard components
│   │   ├── context/         # Auth context
│   │   ├── pages/           # All page components
│   │   ├── services/        # API client (Axios)
│   │   ├── App.jsx          # Router + protected routes
│   │   ├── main.jsx         # React entry
│   │   └── index.css        # Tailwind + custom styles
│   ├── vite.config.js
│   ├── tailwind.config.js
│   └── package.json
└── README.md
```

## Key Design Decisions

- **Career breaks are never penalized** in job matching or skills assessment
- **Transparent scoring** — every match shows a breakdown of how the score was calculated
- **Human oversight** — users can review and re-run any agent's analysis
- **Demo mode by default** — works out of the box without MongoDB or AI credentials
- **Green theme** — dark background with green accent colors throughout
