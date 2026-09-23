# AgentFoundry Core 

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![MCP Compatible](https://img.shields.io/badge/MCP-Enabled-green.svg)](https://modelcontextprotocol.io/)
[![Next.js](https://img.shields.io/badge/Frontend-Next.js%2015-black.svg)](https://nextjs.org/)
[![FastAPI](https://img.shields.io/badge/Backend-FastAPI%20%7C%20Python-009688.svg)](https://fastapi.tiangolo.com/)
[![Docker](https://img.shields.io/badge/Deployment-Docker%20%26%20Compose-2496ED.svg)](https://www.docker.com/)

![AgentFoundry Banner](assets/project_banner.png)

> An opinionated, production-grade template engineered for autonomous agent workflows. Scaffolds novel AI, robotics, and SaaS products from concept to cloud in minutes.

---

##  Architecture Overview

```mermaid
flowchart TD
    subgraph Orchestrator["🧠 System Orchestrator"]
        direction TB
        AI["Claude / Codex / GPT-5"]
    end

    subgraph MCP["🔌 MCP Layer: Context & Tools"]
        direction TB
        FS["Filesystem & Git Inspector"]
        DB["Database Inspector<br/>(Postgres)"]
        DK["Docker & Runtime Control"]
    end

    subgraph Agents["🤖 Agent Personas"]
        direction TB
        PM["Architect & PM"]
        DEV["Full-Stack Developer"]
        QA["Test & Deployment Lead"]
    end

    subgraph Frontend["⚡ Frontend Module"]
        direction TB
        NEXT["Next.js 15 App Router"]
        UI["Tailwind + shadcn/ui"]
    end

    subgraph Backend["⚙️ Backend Module"]
        direction TB
        API["FastAPI + Async"]
        ORM["SQLAlchemy 2.0"]
    end

    Orchestrator --> MCP
    Orchestrator --> Agents
    
    MCP --> Frontend
    MCP --> Backend
    
    Agents --> Frontend
    Agents --> Backend
    
    Frontend <== "OpenAPI / WS" ==> Backend

    classDef orchestrator fill:#6366f1,stroke:#4f46e5,stroke-width:2px,color:#ffffff
    classDef mcp fill:#0ea5e9,stroke:#0284c7,stroke-width:2px,color:#ffffff
    classDef agents fill:#8b5cf6,stroke:#7c3aed,stroke-width:2px,color:#ffffff
    classDef frontend fill:#10b981,stroke:#059669,stroke-width:2px,color:#ffffff
    classDef backend fill:#f59e0b,stroke:#d97706,stroke-width:2px,color:#ffffff

    class Orchestrator orchestrator
    class MCP mcp
    class Agents agents
    class Frontend frontend
    class Backend backend
```

---

##  Key Features

- **Systemic Agent Personas**: Pre-configured system prompts in `.cursorrules`, `.windsurfrules`, and `.agents/` covering product design, architecture diagrams, implementation, and code reviews.
- **Built-in MCP Integration**: Native configurations for Model Context Protocol servers including Postgres, Filesystem, GitHub, and Memory engines.
- **Scaffolded Architecture Engine**: Automated generation scripts for Mermaid.js system architecture diagrams, state machines, and sequence charts.
- **Standardized Monorepo Layout**: Co-located Next.js frontend, Python FastAPI backend, database migrations, and Docker configurations.
- **CI/CD & Deployment Ready**: GitHub Actions pipelines for automated linting, test coverage, semantic container builds, and deployment hooks.

---

##  Repository Structure

```tree
.
├── .agents/                 # Agent personas, prompt playbooks, and checklists
│   ├── 01_ideation.md       # PRD generator and requirements parser
│   ├── 02_architecture.md   # C4 model and Mermaid diagram blueprints
│   ├── 03_implementation.md # TDD patterns and feature implementation guides
│   └── 04_deployment.md     # Production release checklists
├── .cursor/rules/           # Tailored rules for Cursor IDE AI agents
├── .mcp/                    # MCP server configs (Postgres, Git, Docker, Filesystem)
│   └── mcp_config.json
├── backend/                 # FastAPI modern async application
│   ├── app/
│   │   ├── api/             # Versioned REST endpoints
│   │   ├── core/            # Config, security, and logging
│   │   └── models/          # SQLAlchemy and Pydantic schemas
│   ├── tests/
│   └── Dockerfile
├── frontend/                # Next.js 15 with App Router
│   ├── src/
│   │   ├── app/             # Application routes and pages
│   │   ├── components/ui/   # Reusable UI component library (shadcn/ui)
│   │   └── lib/             # API clients and utilities
│   └── Dockerfile
├── docs/                    # Living system documentation
│   ├── architecture/        # Architecture Decision Records (ADRs) and diagrams
│   └── roadmaps/            # Milestone breakdowns and sprint tracking
├── docker-compose.yml       # Local development stack orchestration
└── README.md
```

---

##  Quickstart

### 1. Clone & Bootstrap

```bash
git clone https://github.com/your-username/agentfoundry-core.git my-new-project
cd my-new-project
chmod +x scripts/bootstrap.sh && ./scripts/bootstrap.sh
```

### 2. Configure Environment

```bash
cp .env.example .env
```

### 3. Spin Up Development Stack

```bash
docker compose up -d
```

- Frontend: `http://localhost:3000`
- API Documentation: `http://localhost:8000/docs`

---

##  Agentic SDLC Workflow

1. **Ideation**: Run `@01_ideation.md` with your raw concept to synthesize an engineering PRD, user journeys, and feature prioritization.
2. **Architecture**: Trigger `@02_architecture.md` to produce Mermaid system diagrams and create initial Architecture Decision Records.
3. **Scaffold**: The agent invokes MCP tools to verify environment dependencies and auto-generate schema migrations.
4. **Implementation**: Build modules iteratively using test-driven instructions in `@03_implementation.md`.
5. **Release**: Validate the pre-flight checks in `@04_deployment.md` before merging to main.

---

## License

Distributed under the MIT License. See `LICENSE` for details.
