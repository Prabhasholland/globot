# Globot — Agentic AI for Supply Chain Risk Intelligence

[![CI](https://github.com/Prabhasholland/globot/actions/workflows/ci.yml/badge.svg)](https://github.com/Prabhasholland/globot/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python 3.11](https://img.shields.io/badge/Python-3.11-blue.svg)](https://www.python.org/)
[![React](https://img.shields.io/badge/Frontend-React%20%2B%20Vite-61DAFB.svg)](https://react.dev/)

**From reactive logistics to proactive risk intelligence.**

Globot is an open-source, AI-powered supply chain decision-support platform that helps logistics teams investigate disruptions, evaluate alternative shipping routes, estimate financial exposure, and review compliance requirements through a human-supervised workflow.

When geopolitical tensions, port congestion, or shipping disruptions threaten valuable cargo, Globot brings multiple analytical perspectives together in one workspace.

> **Important:** Globot is a research and demonstration project. Default scenarios use mock or synthetic data. Its outputs are illustrative and must be independently verified before use in real-world financial, compliance, or logistics decisions.

---

## Table of Contents

- [Overview](#overview)
- [The Problem](#the-problem)
- [Our Solution](#our-solution)
- [Core Features](#core-features)
- [Multi-Agent Architecture](#multi-agent-architecture)
- [Technology Stack](#technology-stack)
- [System Architecture](#system-architecture)
- [Getting Started](#getting-started)
- [Configuration](#configuration)
- [Running the Demo](#running-the-demo)
- [Project Structure](#project-structure)
- [Responsible AI](#responsible-ai)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)

## Overview

Global supply chains are vulnerable to geopolitical instability, shipping route disruptions, fluctuating freight costs, port congestion, and complex insurance requirements.

Traditional workflows often require operators to switch between spreadsheets, news feeds, route-planning tools, and lengthy legal documents before making a decision.

Globot explores how agentic AI can bring these activities together into a transparent, human-supervised decision-support workflow.

### Our Mission

To make supply chain disruption analysis more accessible, explainable, and reproducible by combining AI-assisted reasoning, logistics visualization, financial analysis, and human oversight.

## The Problem

Consider a shipping company managing cargo worth millions of dollars when a major maritime corridor becomes unsafe.

The operations team must quickly answer critical questions:

- What has changed, and which shipments could be affected?
- Which alternative routes should be evaluated?
- How could rerouting affect fuel costs and freight expenses?
- What do the relevant insurance policies cover?
- What evidence supports each recommendation?
- Who approves the final operational decision?

Fragmented information makes it difficult to evaluate these questions consistently under pressure.

## Our Solution

Globot provides a unified workspace for reviewing supply chain disruption scenarios.

The platform combines scenario-driven demonstrations, route visualization, risk assessment experiments, compliance document analysis, and approval workflows.

Its multi-agent design separates analytical responsibilities so that different perspectives can be examined before a human operator makes a decision.

## Core Features

### 1. Scenario-Driven Disruption Simulation

Explore reproducible shipping disruption scenarios using local demonstration fixtures and synthetic data.

### 2. Multi-Agent Risk Review

Organize market intelligence, logistics, financial hedging, and compliance analysis into distinct analytical perspectives.

### 3. Interactive Logistics Visualization

Use Deck.gl-based geospatial visualization to inspect ports, shipping routes, and highlighted risk areas.

### 4. Route Comparison

Evaluate alternative shipping routes and review associated risk and cost considerations within the demonstration workflow.

### 5. Financial Exposure Analysis

Experiment with financial impact calculations involving illustrative fuel costs, freight changes, and rerouting expenses.

### 6. Compliance Document Experiments

Explore workflows for retrieving and analyzing relevant sections of insurance and compliance documents.

### 7. Human Approval Workflow

Review a recommendation, inspect its details, and approve or override it through an explicit human-controlled workflow.

The interface is designed for decision support rather than unrestricted autonomous execution.

### 8. Pluggable AI Providers

Support an extensible provider architecture, with Ollama as the default provider described by the project and optional providers configured through server-side environment variables.

Provider availability and supported features depend on the current implementation and configuration.

## Multi-Agent Architecture

Globot organizes its decision-support workflow around five analytical roles.

| Agent | Responsibility |
|---|---|
| Market Sentinel | Reviews disruption signals and market-related information |
| Risk Hedger | Estimates financial exposure using configured assumptions |
| Logistics Orchestrator | Evaluates alternative shipping routes |
| Compliance Manager | Retrieves and analyzes relevant document information |
| Adversarial Reviewer | Challenges proposed recommendations and identifies weaknesses |

The agents represent separate analytical responsibilities. The availability of live data, independent model calls, and fully automated coordination depends on the enabled integrations.

### Example Workflow

1. A user opens a shipping disruption scenario.
2. The system presents the relevant scenario information.
3. The analytical workflow evaluates route, financial, and compliance considerations.
4. Findings are consolidated for review.
5. The user examines the supporting information and uncertainties.
6. A human explicitly approves or overrides the proposed action.

The goal is to make decisions easier to inspect rather than treating an AI-generated answer as automatically correct.

## Technology Stack

### Backend

- Python 3.11
- FastAPI
- REST API architecture

### Frontend

- React
- TypeScript
- Vite
- Deck.gl

### AI and Data

- Ollama for local model inference in the default provider configuration
- Optional model providers where implemented and configured
- Retrieval-augmented generation (RAG) experiments
- Vector search and document retrieval components, where enabled
- Mock and synthetic data for reproducible demonstrations

### Development and Quality

- Git and GitHub
- GitHub Actions
- Python syntax checks
- Frontend production builds
- Automated dependency maintenance

## System Architecture

```text
              Logistics Operator
                      |
                      v
          React + TypeScript + Vite
             Review UI and Map
                      |
                      v
               FastAPI Backend
                      |
          +-----------+-----------+
          |           |           |
          v           v           v
       Scenario    Risk and    Documents and
       Workflow    Routing     Hedging Analysis
          |           |           |
          +-----------+-----------+
                      |
                      v
           Mock / Synthetic Data
           Optional AI Providers
                      |
                      v
          Human Review and Approval
```

This architecture is intended to support incremental development, testing, and the addition of verified data integrations.

## Getting Started

### Prerequisites

Install the following tools before starting:

- Python 3.11
- Node.js 20 or later
- pnpm
- Git

### 1. Clone the Repository

```bash
git clone https://github.com/Prabhasholland/globot.git
cd globot
```

### 2. Configure the Backend

Navigate to the backend directory:

```bash
cd backend
```

Create and activate a virtual environment.

**Windows PowerShell:**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**macOS/Linux:**

```bash
python3.11 -m venv .venv
source .venv/bin/activate
```

Install dependencies:

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

Create your local environment file:

```bash
# Windows
Copy-Item .env.example .env

# macOS/Linux
cp .env.example .env
```

Review the environment variables and configure only the providers and integrations you intend to use.

Start the backend:

```bash
python start_server.py
```

The backend is expected to be available at:

`http://localhost:8000`

### 3. Configure the Frontend

Open another terminal at the repository root:

```bash
cd frontend
```

Install dependencies:

```bash
pnpm install --frozen-lockfile
```

Create the frontend environment file:

```bash
# Windows PowerShell
Copy-Item .env.example .env

# macOS/Linux
cp .env.example .env
```

Start the development server:

```bash
pnpm dev
```

The frontend is expected to be available at:

`http://localhost:5173`

**Note:** Exact startup commands and environment variables should be checked against the current repository files.

## Configuration

Globot uses example environment files to separate configuration from application code.

| File | Purpose |
|---|---|
| `backend/.env.example` | Backend settings and optional AI provider configuration |
| `frontend/.env.example` | Frontend API base URL and public authentication configuration |

### Security Guidelines

- Never commit API keys, private tokens, or production credentials.
- Keep secret values in server-side environment variables.
- Do not expose privileged credentials through frontend environment variables.
- Use verified and appropriately licensed data for real operational deployments.
- Configure authentication, access controls, logging, and approval records before exposing the system to real users.

## Running the Demo

1. Start the backend and frontend.
2. Open `http://localhost:5173/pay`.
3. Select **Watch Demo** to enter the route-selection workflow.
4. Review the default Shanghai-to-Rotterdam scenario.
5. Confirm the route and start the simulation.
6. Inspect the activity feed, route information, and analytical findings.
7. Review the recommendation before using the human approval workflow.

Use demonstration data only for experimentation. An approval action in a local demo must not be interpreted as evidence of a live shipment execution integration.

## Project Structure

```text
globot/
├── backend/
│   ├── data/
│   ├── requirements.txt
│   ├── start_server.py
│   └── .env.example
├── frontend/
│   ├── src/
│   ├── package.json
│   ├── pnpm-lock.yaml
│   └── .env.example
├── docs/
│   ├── ROADMAP.md
│   └── OPENAI_API_PLAN.md
├── .github/
│   └── workflows/
├── LICENSE
├── CONTRIBUTING.md
├── SECURITY.md
├── CODE_OF_CONDUCT.md
└── README.md
```

This is a representative structure. Check the repository for the exact current paths and filenames.

## Responsible AI

Globot is designed as a human-supervised decision-support system.

AI-generated recommendations may be incomplete, outdated, or incorrect. Financial estimates depend on their input assumptions. Document analysis does not replace professional legal review, and satellite imagery alone cannot establish that a port or shipping corridor is unsafe.

Before operational use, the system requires reliable data sources, appropriate access controls, independent evaluation, documented uncertainty, and human authorization for consequential actions.

## Roadmap

Planned improvements include:

- More comprehensive automated scenario and API tests
- Evidence and provenance records for recommendations
- Optional integrations with licensed market and news sources
- Vessel tracking through an appropriate AIS provider
- Satellite imagery workflows using suitable imagery services
- Improved document retrieval and evaluation
- Stronger authentication and audit controls
- Additional demonstrations for air freight and rail logistics
- Better monitoring, error handling, and reproducible deployments

Roadmap items are proposed improvements and should not be interpreted as currently available functionality.

## Contributing

Contributions are welcome.

You can help by:

- Reporting bugs and suggesting improvements
- Adding reproducible disruption scenarios
- Improving documentation and test coverage
- Evaluating risk assessment workflows
- Developing optional data-provider integrations
- Improving accessibility and visualization

Before contributing, review the repository's contribution guidelines and security policy.

- [Contribution Guidelines](CONTRIBUTING.md)
- [Security Policy](SECURITY.md)
- [Code of Conduct](CODE_OF_CONDUCT.md)
- [Support](SUPPORT.md)
- [Governance](GOVERNANCE.md)

## License

Globot is distributed under the MIT License. See [LICENSE](LICENSE) for details.

## Acknowledgements

Globot builds on the broader open-source ecosystem for Python, FastAPI, React, geospatial visualization, and AI-assisted application development.

## Final Note

Globot explores how agentic AI can make complex supply chain disruption analysis more transparent, reproducible, and accountable.

**Our vision: better intelligence for better decisions, with humans remaining responsible for the outcomes.**

---

**Maintained by:** [Prabhas Banavath](https://github.com/Prabhasholland)

**Repository:** https://github.com/Prabhasholland/globot
