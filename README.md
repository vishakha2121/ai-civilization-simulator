# 🌍 AI Civilization Simulator

> **Watch an entire civilization rise, trade, war, innovate, and evolve — all powered by autonomous AI agents.**

![Status](https://img.shields.io/badge/status-active--development-success)
![Python](https://img.shields.io/badge/Backend-Python%20%7C%20FastAPI-blue)
![React](https://img.shields.io/badge/Frontend-React%20%7C%20Tailwind-cyan)
![LLM](https://img.shields.io/badge/LLM-Google%20Gemini-orange)
![License](https://img.shields.io/badge/License-MIT-purple)

## 📖 Table of Contents
1. [What Is This Project?](#-what-is-this-project)
2. [Core Architecture](#-the-core-idea--hybrid-intelligence)
3. [Key Features](#-key-features)
4. [Tech Stack](#-tech-stack)
5. [Project Structure](#-project-structure)
6. [Database Schema](#-database-schema)
7. [API Endpoints](#-api-endpoints)
8. [Quick Start Guide](#-quick-start-guide)
9. [LLM Optimization Strategy](#-llm-optimization-strategy)
10. [What Makes This Special?](#-what-makes-this-special)
11. [Roadmap](#-roadmap)
12. [Documentation](#-documentation)
13. [Troubleshooting](#-troubleshooting)
14. [License](#-license)

---

## 🚀 What Is This Project?

**AI Civilization Simulator** is a research-oriented, practice-scale simulation lab where **thousands of autonomous AI agents** interact in a persistent virtual world to form **governments, economies, societies, cultures, wars, and technological progress** — none of which are hardcoded. 

Every alliance, rebellion, invention, and collapse **emerges** from the bottom-up interactions of agents following local rules and making intelligent decisions. This project is built to explore the boundaries of **Generative Agents**, **Complex Adaptive Systems**, and **Multi-Agent Reinforcement Learning**.

This project deeply explores three research areas:
- **Emergent Intelligence:** Complex civilization-level behavior arising from simple, localized agent rules.
- **Agent Society:** How individual agents form social structures, hierarchies, trade agreements, and institutions over time.
- **Large Scale Simulation:** Running tens of thousands of agents efficiently in real-time on commodity hardware (CPU-only).

---

## 🧠 The Core Idea — Hybrid Intelligence

Running **millions** of LLM-powered agents is economically and computationally impossible on consumer hardware. Gemini API has strict rate limits, and LLM inference is slow. So this simulator uses a **Hybrid Architecture**:

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **95% of Agents** | Fast rule-based logic (NumPy-vectorized) | Movement, resource gathering, basic combat, reproduction, pathfinding. |
| **5% of Agents** | **Google Gemini LLM** (batched + cached) | Leaders, diplomats, and scientists making high-level strategic decisions (e.g., declaring war, signing treaties, unlocking techs). |

**Why this works:**
This design achieves **emergent civilization behavior** at **10,000+ agents** on a **CPU-only laptop**. It reduces LLM API calls by ~90% through intelligent batching, prompt caching, and rule-based fallbacks, ensuring the simulation runs smoothly without hitting API rate limits.

---

## ✨ Key Features

- 🏛️ **Emergent Governments** — Elections, policies, coups, and revolutions form organically based on agent happiness and resource distribution.
- 💰 **Dynamic Economies** — Trade networks, resource scarcity, wealth inequality, inflation, and market crashes emerge naturally.
- ⚔️ **Organic Wars** — Conflicts are not scripted; they trigger due to resource disputes, overpopulation, or aggressive leaders.
- 🧬 **Cultural Evolution** — Traditions, values, and art spread through agent interactions and social memes.
- 🔬 **Technology Tree** — Scientific agents unlock discoveries, propelling the civilization from the Stone Age to the Space Age.
- 🤝 **AI Diplomacy** — LLM-powered treaties, alliances, trade pacts, and betrayals between different civilizations.
- 📊 **Real-Time Analytics** — Live dashboards tracking population, economy, tech progress, and war casualties.
- 🎮 **Beautiful Sci-Fi UI** — Dark-themed, animated React dashboard with a live 2D world map and glassmorphism design.
- 🔄 **WebSocket Streaming** — Real-time tick updates broadcasted to the frontend without page refresh.
- 💾 **Snapshot & Replay** — Save the exact state of the simulation, replay history, and export analytical reports.

---

## 🛠️ Tech Stack

**Backend:**
- **Framework:** Python, FastAPI, Uvicorn
- **Simulation Engine:** Custom Tick Scheduler (AsyncIO), NumPy
- **Database ORM:** SQLAlchemy (SQLite for dev, PostgreSQL ready)
- **AI Integration:** Google Gemini API (`google-generativeai`)
- **Real-time:** WebSockets

**Frontend:**
- **Framework:** React 18, Vite
- **Styling:** TailwindCSS, Framer Motion (animations)
- **State Management:** Zustand
- **Data Visualization:** Recharts, HTML5 Canvas
- **Icons:** Lucide React

**DevOps & Tools:**
- **Environment:** `.env` configs, Git
- **Testing:** pytest (backend)
- **Deployment:** Docker Compose (optional)

---

## 📁 Project Structure

```text
ai-civilization-simulator/
│
├── backend/                   # FastAPI Backend
│   ├── app/
│   │   ├── api/               # REST API Routers (agents, sim, events)
│   │   ├── core/              # Simulation Engine, Tick Scheduler
│   │   ├── agents/            # Rule-based & LLM Agent classes
│   │   ├── systems/           # Economy, War, Government, Tech systems
│   │   ├── llm/               # Gemini Client, Prompt Batching, Cache
│   │   ├── db/                # SQLAlchemy Models & Schemas
│   │   └── services/          # Business logic
│   ├── tests/                 # Pytest suite
│   ├── requirements.txt
│   └── main.py                # Entry point
│
├── frontend/                  # React Frontend
│   ├── src/
│   │   ├── api/               # Axios API clients
│   │   ├── components/        # UI Components (Charts, Map, Cards)
│   │   ├── pages/             # Dashboard, Agents, Analytics
│   │   ├── store/             # Zustand global state
│   │   └── utils/             # Helpers, formatters
│   ├── package.json
│   └── tailwind.config.js
│
├── database/                  # SQL migrations & seed data
├── docs/                      # In-depth documentation
└── README.md