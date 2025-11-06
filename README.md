# 🧠 visio-director

> An AI-powered creative director that understands brand strategy, visual intent, and audience psychology to generate vision-aligned design prompts for tools like Lovart.ai, Runway, Lovable, and Luma.ai.

[![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

---

## 📌 Project Overview

`visio-director` is an intelligent, multimodal prompt engineering system that simulates the thinking patterns of a world-class **creative director**. It uses **Mind Chain of Thought (M-CoT)** reasoning powered by **LangGraph** to translate strategic business goals into stylistically rich and platform-optimized visual prompts.

Designed for marketers, branding teams, and visual designers, this AI agent goes beyond image generation—it **understands design intention**, **interprets brand tone**, and **adapts to platform-specific prompt grammars**.

---

## ✨ Key Features

- 🧠 **Mind Chain of Thought Reasoning (M-CoT)**
  Multi-step cognitive modeling that mimics how a creative director breaks down a brief into actionable visual concepts.

- 📊 **Strategic Brief Analyzer**
  Ingests brand information, commercial context, and audience targeting to guide prompt construction.

- 🎨 **Design Language Interpreter**
  Translates abstract concepts (e.g. "premium yet playful", "organic minimalism") into visual grammar and structured input.

- 🖼️ **Multimodal Prompt Generator**
  Outputs platform-optimized prompts for:
  - **Image**: `Midjourney` / `Lovart.ai`
  - **Video**: `Runway ML` / `Kling` / `Luma.ai`
  - **3D**: `Luma.ai NeRF` / `Lovart 3D`
  - **UI/UX**: `Lovable.dev`
  - **Content**: `GPT-4` / `Claude`

- 🔁 **Visual Feedback Loop (VFL)**
  Enables iterative refinement based on visual outputs and semantic brand alignment.

- 🗄️ **Brand Memory System**
  Uses **PostgreSQL + pgvector** for semantic brand profiles and prompt history with vector search capabilities.

---

## 🔧 Technologies Used

| Stack        | Purpose                                   |
|--------------|-------------------------------------------|
| **Python 3.11+** | Core logic, LLM integration, reasoning engine |
| **LangGraph** | Workflow graph structure for multi-stage reasoning |
| **OpenAI GPT-4** | Primary LLM for brand strategy understanding |
| **Claude 2.1** | Backup LLM for semantic reasoning |
| **PostgreSQL + pgvector** | Brand profiles, prompt history, semantic search |
| **FastAPI** | REST API backend |
| **React / Next.js** | Web UI (optional) |
| **Docker** | Containerization and deployment |

---

## 📂 Project Structure

```bash
visio-director/
├── src/
│   ├── main/
│   │   ├── python/
│   │   │   ├── agents/          # LangGraph M-CoT reasoning chains
│   │   │   ├── adapters/        # Platform-specific prompt adapters
│   │   │   ├── core/            # Brand DNA engine + reasoning core
│   │   │   ├── api/             # FastAPI endpoints
│   │   │   ├── models/          # SQLAlchemy + Pydantic models
│   │   │   ├── services/        # Business logic services
│   │   │   └── utils/           # Shared utilities
│   │   └── resources/
│   │       ├── config/          # Configuration files
│   │       └── data/            # Sample brand data
│   └── test/
│       ├── unit/                # Unit tests
│       ├── integration/         # Integration tests
│       └── fixtures/            # Test data
├── data/
│   ├── raw/                     # Raw brand datasets
│   ├── processed/               # Cleaned and transformed data
│   ├── external/                # External data sources
│   └── temp/                    # Temporary processing files
├── notebooks/
│   ├── exploratory/             # Data exploration notebooks
│   ├── experiments/             # Prompt experiments
│   └── reports/                 # Analysis reports
├── experiments/
│   ├── configs/                 # Experiment configurations
│   ├── results/                 # Experiment results and metrics
│   └── logs/                    # Prompt experiment logs
├── models/
│   ├── trained/                 # Fine-tuned models (future)
│   ├── checkpoints/             # Model checkpoints
│   └── metadata/                # Model metadata
├── ui/
│   └── frontend/                # React/Next.js web UI (optional)
├── docs/
│   ├── api/                     # API documentation
│   ├── user/                    # User guides
│   └── dev/                     # Developer documentation
├── CLAUDE.md                    # AI development guidelines
├── README.md                    # This file
├── pyproject.toml               # Poetry dependencies
├── docker-compose.yml           # Docker services
└── .gitignore                   # Git ignore patterns
```

---

## 🚀 Quick Start

### Prerequisites

- Python 3.11+
- Poetry (Python package manager)
- Docker & Docker Compose (for PostgreSQL + pgvector)
- OpenAI API Key

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/visio-director.git
   cd visio-director
   ```

2. **Install dependencies**
   ```bash
   poetry install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   # Edit .env and add your API keys
   ```

4. **Start PostgreSQL + pgvector**
   ```bash
   docker-compose up -d
   ```

5. **Run database migrations**
   ```bash
   poetry run alembic upgrade head
   ```

6. **Start the API server**
   ```bash
   poetry run uvicorn src.main.python.api.main:app --reload
   ```

7. **Open the API documentation**
   ```
   http://localhost:8000/docs
   ```

---

## 🧪 Sample Use Case

### Input (Brand Brief):

```json
{
  "brand": "eco-friendly skincare startup",
  "audience": "millennial women 25-35, urban, wellness-conscious",
  "style_keywords": ["natural", "glow", "clean", "organic"],
  "platform": "Runway",
  "asset_type": "social campaign visual"
}
```

### Output Prompt (for Runway):

```text
A clean and minimal flat-lay of skincare products on natural stone,
soft pastel background, morning sunlight with subtle shadows, glass
containers with golden lids, surrounded by eucalyptus leaves.
Aesthetic mood: organic luxury. Photographic style with soft tones,
slight grain, optimized for Instagram carousel format.
```

---

## 🧠 Prompt Design Philosophy

This system is not just "prompt stuffing"—it's based on high-level **creative strategy translation**. It integrates:

* **Brand identity logic** - Understanding core brand values and positioning
* **Audience emotional resonance** - Targeting psychological triggers
* **Visual semiotics** - Design language and symbolic meaning
* **Platform-specific constraints** - Optimized for each generation tool

---

## 📊 Development Roadmap

### Phase 1: Core Engine (Weeks 1-3) ✅ IN PROGRESS
- [ ] Prompt Architecture design
- [ ] LangGraph M-CoT reasoning chain
- [ ] PostgreSQL + pgvector schema
- [ ] Brand DNA analyzer

### Phase 2: Platform Integration (Weeks 4-6)
- [ ] Platform Adapters (Lovart, Runway, Luma, Lovable)
- [ ] REST API / GraphQL endpoints
- [ ] Brand strategy analyzer

### Phase 3: Frontend & UX (Weeks 7-8)
- [ ] Web UI (React/Next.js)
- [ ] Visual Feedback Loop (VFL)

### Phase 4: Deployment & Optimization (Weeks 9-10)
- [ ] Docker + Cloud deployment (GCP/AWS)
- [ ] Cost optimization (Token management)
- [ ] Monitoring & logging

---

## 🔮 Future Plans

* [ ] Voice-to-brief capability
* [ ] Moodboard-to-prompt conversion
* [ ] Integration with Figma and Notion
* [ ] Automatic tone-matching across multiple platforms
* [ ] Fine-tuned models for specific brand industries
* [ ] Multi-language brand brief support

---

## 🤝 Contributing

Contributions are welcome! Please read our [Contributing Guidelines](CONTRIBUTING.md) before submitting a Pull Request.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- Inspired by the creative direction methodologies of leading design agencies
- Built with [LangGraph](https://github.com/langchain-ai/langgraph) for advanced reasoning workflows
- Powered by [OpenAI GPT-4](https://openai.com/gpt-4) for strategic understanding

---

## 📧 Contact

For questions or support, please open an issue or contact the maintainers.

---

**Made with ❤️ by the visio-director team**

**Powered by TaskMaster + Linus Philosophy** 🤖⚔️
