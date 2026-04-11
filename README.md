# 🔴🛡️ RedBlue AI

### Autonomous Red Team Agent with Assisted Remediation

> **Attack. Detect. Fix. Verify. Repeat.**

Built at **Government Engineering College Thrissur** during **Hack Quest 2026** as part of **Hack@Arch 4.0**

---

## 📌 Overview

**RedBlue AI** is an AI-driven cybersecurity system that autonomously attacks your web application, explains every vulnerability it finds, suggests precise fixes, and verifies the patch held — all in one continuous human-supervised loop.

Security testing is expensive, slow, and rare. Most developers ship code without any real vulnerability checks — not because they don't care, but because the tools available require a dedicated security team. RedBlue AI changes that.

```
Red Agent (LLM) → Vuln Report → Blue Agent (Fix Maps) → User Approval → Re-run Red → ✅ Secured
```

---

## ✨ Features

- 🔴 **Autonomous Red Agent** — LLM-powered attacker that scans endpoints, plans attacks, executes real payloads (SQLi, open admin panel), and produces structured vulnerability reports
- 🤖 **LLM Vulnerability Reasoning** — every finding explains *why* it's vulnerable and *how* it was exploited, not just what was found
- 🛡️ **Blue Agent Fix Suggestions** — automatically maps each vulnerability to a precise, actionable remediation with impact analysis
- 👤 **Human-in-the-Loop Approval Gate** — no patch is applied without explicit user sign-off, ever
- 🔁 **Post-fix Retest Verification** — Red Agent re-runs on patched endpoints to confirm every exploit is blocked
- 📡 **Animated Attack Timeline** — full narrative log of every step from scan to secured with auto-play
- 📊 **Live Security Dashboard** — real-time status, 5-step flow stepper, and endpoint state tracking
- 📱 **Fully Responsive** — works seamlessly across desktop and mobile

---

## 🖥️ Pages

| Route | Page | Description |
|---|---|---|
| `/` | Home | Hero, How It Works, CTA, Future Scaling Roadmap |
| `/dashboard` | Dashboard | Status card, flow stepper, action buttons, endpoint preview |
| `/red-report` | Red Report | Vulnerability cards with LLM reasoning toggle |
| `/fix-suggestions` | Fix Suggestions | Blue Agent fix cards with per-fix and apply-all approval |
| `/logs` | Logs | Animated timeline with Auto-Play button |

---

## 🧠 How It Works

```
1. Red Agent scans target app endpoints (/login, /admin)
2. Executes attack payloads — SQL injection, direct route access
3. Generates structured vulnerability report with LLM reasoning
4. Blue Agent reads report → maps each finding to a fix template
5. User reviews fix suggestions and approves patches
6. Fixes are applied to the target app
7. Red Agent re-runs to verify exploits no longer succeed
8. System marked ✅ Secured
```

---

## 🛠️ Tech Stack

**Frontend**
- [Next.js 14](https://nextjs.org/) — App Router, file-based routing
- [TypeScript](https://www.typescriptlang.org/) — type safety
- [Tailwind CSS v3](https://tailwindcss.com/) — utility-first styling
- [React 18](https://react.dev/) — `useState`, `useEffect`, `useRef`
- [Google Fonts](https://fonts.google.com/) — Syne + Space Mono

**Backend & AI**
- [Python](https://www.python.org/) — core agent logic
- [FastAPI](https://fastapi.tiangolo.com/) — REST API server
- [LangChain](https://www.langchain.com/) — agent orchestration loop
- [OpenAI / Anthropic LLM](https://openai.com/) — Red Agent reasoning & attack planning
- [SQLite](https://www.sqlite.org/) — vulnerable demo target app database

**Target Demo App**
- [Flask](https://flask.palletsprojects.com/) — intentionally vulnerable app (`/login` SQLi + `/admin` no auth)

---

## 🚀 Getting Started

### Prerequisites
- Node.js 18+
- npm

### Frontend Setup

```bash
# Clone the repository
git clone https://github.com/THARUN-KRSHN/redblue-ai.git
cd redblue-ai/frontend

# Install dependencies
npm install

# Start development server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Backend Setup

```bash
cd backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Add your OpenAI / Anthropic API key to .env

# Start the API server
uvicorn main:app --reload
```

API runs at [http://localhost:8000](http://localhost:8000)

---

## 📁 Project Structure

```
redblue-ai/
│
├── frontend/
│   ├── app/
│   │   ├── layout.tsx             ← Root layout (Navbar + Footer)
│   │   ├── globals.css            ← Global styles + animations
│   │   ├── page.tsx               ← Home / Landing page
│   │   ├── dashboard/page.tsx     ← Main dashboard
│   │   ├── red-report/page.tsx    ← Red Agent report
│   │   ├── fix-suggestions/page.tsx ← Blue Agent fixes
│   │   └── logs/page.tsx          ← Attack timeline
│   ├── components/
│   │   └── layout/
│   │       ├── Navbar.tsx
│   │       └── Footer.tsx
│   ├── lib/
│   │   └── demoData.ts            ← Demo JSON data
│   └── package.json
│
├── backend/
│   ├── agents/
│   │   ├── red_agent.py           ← Red Agent attack logic
│   │   └── blue_agent.py          ← Blue Agent fix mapper
│   ├── target_app/
│   │   └── app.py                 ← Vulnerable Flask demo app
│   ├── main.py                    ← FastAPI entry point
│   └── requirements.txt
│
└── README.md
```

---

## 🔒 Vulnerabilities Demonstrated

### 1. SQL Injection — `/login`
| Field | Detail |
|---|---|
| Severity | 🔴 High |
| Payload | `' OR 1=1 --` |
| Result | Authentication completely bypassed |
| Fix | Parameterized queries / ORM sanitization |

### 2. Open Admin Panel — `/admin`
| Field | Detail |
|---|---|
| Severity | 🟡 Medium |
| Payload | Direct URL navigation |
| Result | Full admin access without credentials |
| Fix | Auth middleware with 401 redirect |

---

## 🗺️ Roadmap

**Phase 1 — Hackathon Demo** ✅
- Two vulnerability types end-to-end
- Full UI dashboard with attack → report → fix → verify flow

**Phase 2 — Feature Expansion**
- XSS, CSRF, IDOR, SSRF attack modules
- Auto-generate fix PRs via GitHub integration
- CVSS-based risk scoring and prioritization

**Phase 3 — CI/CD Integration**
- GitHub Action — run RedBlue on every pull request
- Block merges on critical vulnerability detection

**Phase 4 — SaaS Platform**
- Multi-tenant platform for teams and enterprises
- Per-project dashboards, scan scheduling, compliance reporting

---

## 👥 Team

Built at **Government Engineering College Thrissur** · **Hack Quest 2026** · **Hack@Arch 4.0**

| Name | Role |
|---|---|
| **Jhon** | Red Agent — attack planning, payload execution & vulnerability detection |
| **Alvi** | Blue Agent — fix mapping, remediation templates & impact analysis |
| **Minhaj** | Overall integration — agent pipeline, API orchestration & system flow |
| **Tharun Krishna** | Frontend design & development — dashboard UI, responsive layout & demo experience |

---

## ⚠️ Disclaimer

RedBlue AI is built for **educational and demonstration purposes only**. The vulnerable target application is intentionally insecure and is designed solely to demonstrate how the Red Agent identifies and the Blue Agent remediates real-world attack vectors. Do not deploy the target demo app in any production or public environment.

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

<p align="center">
  <strong>RedBlue AI</strong> — The future of AppSec isn't a quarterly audit. It's a continuous, intelligent loop. 🔴🛡️
</p>
