# 🌍 AI Civilization Simulator

> **Watch an entire civilization rise, trade, war, innovate, and evolve — all powered by autonomous AI agents.**

## 🚀 What Is This Project?

**AI Civilization Simulator** is a research-oriented, practice-scale simulation lab where **thousands of autonomous AI agents** interact in a persistent virtual world to form **governments, economies, societies, cultures, wars, and technological progress** — none of which are hardcoded. Every alliance, rebellion, invention, and collapse **emerges** from the bottom-up interactions of agents following local rules and making intelligent decisions.

This project explores three deep research areas:
- **Emergent Intelligence** — Complex civilization-level behavior arising from simple agent rules.
- **Agent Society** — How individual agents form social structures, hierarchies, and institutions.
- **Large Scale Simulation** — Running tens of thousands of agents in real-time on commodity hardware.

## 🧠 The Core Idea — Hybrid Intelligence

Running **millions** of LLM-powered agents is economically and computationally impossible on consumer hardware. So this simulator uses a **hybrid architecture**:

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **95% of agents** | Fast rule-based logic (NumPy-vectorized) | Movement, resource gathering, reproduction, basic combat |
| **5% of agents** | **Google Gemini LLM** (batched + cached) | Leaders, diplomats, scientists making high-level strategic decisions |

This design achieves **emergent civilization behavior** at **10,000+ agents** on a **CPU-only laptop**, while reducing LLM API calls by ~90% through intelligent batching, caching, and rule-based fallbacks.

## ✨ Key Features

- 🏛️ **Emergent Governments** — Elections, policies, coups, and revolutions form organically.
- 💰 **Dynamic Economies** — Trade networks, resource scarcity, wealth inequality, and market crashes.
- ⚔️ **Organic Wars** — Conflicts triggered by resource disputes, not scripts.
- 🧬 **Cultural Evolution** — Traditions, values, and art spread through agent interactions.
- 🔬 **Technology Tree** — Discoveries unlocked by scientific agents, propelling civilization forward.
- 🤝 **AI Diplomacy** — LLM-powered treaties, alliances, and betrayals between civilizations.
- 📊 **Real-Time Analytics** — Live dashboards for population, economy, tech, and war stats.
- 🎮 **Beautiful Sci-Fi UI** — Dark-themed, animated React dashboard with live world map.
- 🔄 **WebSocket Streaming** — Real-time tick updates without page refresh.
- 💾 **Snapshot & Replay** — Save simulation state, replay history, export reports.

## 🛠️ Tech Stack

**Backend:** Python · FastAPI · SQLAlchemy · SQLite · NumPy · Google Gemini API · WebSockets
**Frontend:** React · Vite · TailwindCSS · Zustand · Recharts · Framer Motion · Lucide Icons
**Database:** SQLite (dev-ready) with PostgreSQL migration path
**DevOps:** Docker Compose · `.env` configs · pytest test suite

## 🎯 What Makes This Special?

1. **Honest Scope** — Instead of claiming impossible "millions," the architecture is documented to scale, with a working 10K–50K implementation on CPU.
2. **LLM Cost Optimization** — Batching (10 agents/prompt), prompt caching, and rule-based fallback reduce Gemini calls by 90%.
3. **Emergent Behavior Demonstrated** — Wars, alliances, and technological leaps arise *unscripted* from agent interactions.
4. **Interview-Grade Documentation** — Full architecture diagrams, LLM strategy, and simulation design docs included in `/docs`.
5. **Stunning Visual Design** — The dashboard isn't just functional; it's a *showcase* of real-time systems UI craft.

## 🚦 Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/vishakha2121/ai-civilization-simulator.git
cd ai-civilization-simulator

cd backend
python -m venv venv
# Windows
venv\Scripts\activate
# Mac/Linux
source venv/bin/activate

pip install -r requirements.txt
cp .env.example .env
# Add your GEMINI_API_KEY to .env
python scripts/init_db.py
uvicorn main:app --reload

cd ../frontend
npm install
npm run dev