# EduMantri - Intelligent Tutoring System

An AI-powered educational platform that leverages multi-agent systems and Retrieval Augmented Generation (RAG) to provide personalized learning experiences. EduMantri helps students understand concepts, solve problems, and generate study materials through specialized AI agents.

## 📋 Table of Contents

- [Features](#features)
- [Project Structure](#project-structure)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Setup Instructions](#setup-instructions)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Project Components](#project-components)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

### Core Capabilities

- **Multi-Agent System**: Specialized agents for different learning scenarios
  - **Doubts Agent**: Handles student questions using active recall and misconception identification
  - **Generation Agent**: Creates flash cards, practice questions, and summaries
  - **Problem Solver Agent**: Provides step-by-step solutions with concept explanations
  - **Retrieval Agents**: Fetches relevant information from multiple sources

- **RAG Pipeline**: Retrieval Augmented Generation with FAISS indexing for accurate, context-aware responses

- **Content Integration**: 
  - Document processing and analysis
  - Web scraping for educational content
  - YouTube content extraction
  - GitHub repository integration

- **Safety & Guardrails**: Content filtering and validation to ensure appropriate educational material

- **Session Management**: Persistent user sessions for continuity in learning experiences

## 🏗️ Project Structure

```
EduMantri/
├── my-react-app/                 # Frontend (React + Vite)
│   ├── src/
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   ├── Component/
│   │   │   ├── Dashboard.jsx
│   │   │   ├── LandingPage.jsx
│   │   │   └── Workspace.jsx
│   │   └── assets/
│   ├── index.html
│   ├── vite.config.js
│   ├── eslint.config.js
│   └── package.json
│
└── Server/                        # Backend (Python + FastAPI)
    ├── main.py                   # FastAPI application entry point
    ├── Agent/                    # AI Agents
    │   ├── Host_agent.py         # Main orchestrator interface
    │   ├── Orchestrator.py       # Request routing and coordination
    │   ├── Doubts_agent/         # Question handling agent
    │   ├── GenerationAgent/      # Content generation
    │   ├── Problem_solver_agent/ # Problem solving
    │   └── GeneralAgents/        # Retrieval agents
    ├── Services/                 # Core services
    │   ├── ChainsHub.py         # Chain orchestration
    │   ├── Session.py           # Session management
    │   ├── models/              # Data models
    │   └── utils/               # Utilities (chunking, retrieval, database)
    ├── mcp_tools/               # MCP integration tools
    │   ├── docTool/             # Document processing
    │   ├── githubTool/          # GitHub integration
    │   ├── webTool/             # Web scraping
    │   └── YoutubeTool/         # YouTube extraction
    ├── Guardrail/               # Content safety
    │   └── guardrail.py
    ├── prompts/                 # LLM prompts
    ├── faiss_index/             # Vector database
    ├── oldFiles/                # Legacy code
    ├── requirements.txt
    └── README.md
```

## 🏛️ Architecture

### System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Frontend (React)                         │
│        Dashboard | LandingPage | Workspace                 │
└──────────────────────┬──────────────────────────────────────┘
                       │ HTTP/REST
                       ▼
┌─────────────────────────────────────────────────────────────┐
│               FastAPI Backend (main.py)                     │
│                   /chat endpoint                            │
└──────────────────────┬──────────────────────────────────────┘
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
    ┌────────┐    ┌──────────┐    ┌────────┐
    │ Host   │    │Orchestr- │    │Session │
    │ Agent  │───▶│ator      │◀───│Manager │
    └────────┘    └────┬─────┘    └────────┘
                       │
         ┌─────────────┼─────────────┬──────────────┐
         ▼             ▼             ▼              ▼
    ┌─────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐
    │ Doubts  │  │Generation│  │ Problem  │  │Retrieval │
    │ Agent   │  │ Agent    │  │ Solver   │  │ Agents   │
    └────┬────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘
         │            │             │             │
         └────────────┼─────────────┴─────────────┘
                      │
         ┌────────────┼────────────┐
         ▼            ▼            ▼
    ┌────────┐  ┌──────────┐  ┌──────────┐
    │ RAG    │  │ Guardrail│  │ MCP Tools│
    │ FAISS  │  │ Content  │  │(Web,Doc, │
    │ Index  │  │ Filter   │  │GitHub,YT)│
    └────────┘  └──────────┘  └──────────┘
```

### Agent Workflow

1. **User Query** → FastAPI `/chat` endpoint
2. **Session Manager** → Retrieves/creates user session context
3. **Orchestrator** → Routes query to appropriate agent
4. **Specialized Agents** → Process query with specific logic
5. **RAG Pipeline** → Retrieves relevant context from FAISS index
6. **Guardrail** → Validates response safety
7. **Response** → Returns answer with follow-up suggestions

## 🛠️ Tech Stack

### Frontend
- **React 19** - UI library
- **Vite 7** - Build tool and dev server
- **Tailwind CSS 4** - Utility-first CSS framework
- **Material-UI 7** - Component library
- **Emotion** - CSS-in-JS styling

### Backend
- **FastAPI** - Web framework
- **Python 3.x** - Language
- **LangChain** - LLM framework (inferred)
- **FAISS** - Vector search library
- **Pydantic** - Data validation

### Content Sources
- Document processing
- Web scraping
- YouTube API integration
- GitHub API integration

## 📋 Prerequisites

### Frontend
- Node.js 16+ 
- npm or yarn

### Backend
- Python 3.8+
- pip (Python package manager)
- (Optional) Virtual environment tool (venv, conda)

## 💻 Installation

### Frontend Setup

```bash
cd my-react-app

# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Run linting
npm run lint
```

**Frontend will run on**: `http://localhost:5173` (default Vite port)

### Backend Setup

```bash
cd Server

# Create virtual environment (recommended)
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Start FastAPI server
python main.py
```

**Backend will run on**: `http://localhost:8000` (FastAPI default)

## 🚀 Setup Instructions

### 1. Clone/Navigate to Project

```bash
cd EduMantri
```

### 2. Environment Configuration

Create a `.env` file in the `Server/` directory with any required API keys:

```env
# Example environment variables
# OPENAI_API_KEY=your_key_here
# COHERE_API_KEY=your_key_here
# HUGGINGFACE_API_KEY=your_key_here
```

### 3. Database/Index Setup

The FAISS index is pre-initialized at `Server/faiss_index/index.faiss`. To rebuild:

```bash
cd Server
python Services/utils/createDataBase.py
```

### 4. Concurrently Run Frontend and Backend

**Option A: Terminal Tabs**
- Terminal 1: `cd my-react-app && npm run dev`
- Terminal 2: `cd Server && python main.py`

**Option B: Using concurrently (install globally)**
```bash
npm install -g concurrently
concurrently "cd my-react-app && npm run dev" "cd Server && python main.py"
```

## 📡 Usage

### 1. Open Application

Visit `http://localhost:5173` in your browser

### 2. User Flows

#### Ask a Question (Doubts Agent)
1. Navigate to Dashboard/Workspace
2. Type your question
3. System identifies misconceptions and provides active recall prompts
4. View step-by-step worked solutions

#### Generate Study Materials (Generation Agent)
1. Select topic or provide concept
2. Choose material type:
   - Flash cards
   - Practice questions
   - Summaries
3. Review and download generated content

#### Solve Problems (Problem Solver Agent)
1. Upload or describe a problem
2. System breaks down solution into steps
3. Explains underlying concepts
4. Provides related practice problems

## 🔌 API Endpoints

### POST `/chat`

**Request:**
```json
{
  "query": "What is photosynthesis?"
}
```

**Response:**
```json
{
  "response": "Photosynthesis is the process by which plants convert light energy into chemical energy...",
  "followups": [
    "What are the light-dependent reactions?",
    "How does the Calvin cycle work?",
    "What is the role of chlorophyll?"
  ]
}
```

## 🧠 Project Components

### Agent System

| Agent | Purpose | Subcomponents |
|-------|---------|---------------|
| **Host Agent** | Main entry point, session initialization | N/A |
| **Orchestrator** | Route queries to appropriate agent | N/A |
| **Doubts Agent** | Handle questions & misconceptions | Active Recall, Misconception Detection, Worked Solutions |
| **Generation Agent** | Create study materials | Flash Cards, Practice Questions, Summaries |
| **Problem Solver** | Solve complex problems | Concept Solver, Problem Solver, Comparison |
| **Retrieval Agents** | Fetch contextual information | Document Retrieval, Web Search |

### Services

| Service | Function |
|---------|----------|
| **ChainsHub** | Orchestrate LLM chains and workflows |
| **Session** | Manage user sessions and context |
| **Chunking** | Split documents into processable chunks |
| **Retrieval** | Query FAISS index for relevant content |
| **Database** | Create and manage FAISS vector index |

### MCP Tools

| Tool | Function |
|------|----------|
| **docTool** | Process and extract text from documents |
| **webTool** | Scrape educational websites |
| **YoutubeTool** | Extract transcripts from YouTube videos |
| **githubTool** | Fetch code examples from repositories |

## 🔐 Security & Safety

- **Guardrail System**: Content filtering to ensure educational appropriateness
- **CORS Configuration**: Enabled for development (configure for production)
- **Input Validation**: Pydantic models validate all API requests
- **Session Management**: User sessions isolated and tracked

## 📦 Dependencies

### Frontend
- React 19.2.0
- Vite 7.3.1
- Tailwind CSS 4.2.1
- Material-UI 7.3.9
- Emotion 11.14.0

### Backend
See `Server/requirements.txt` for complete list. Key dependencies include:
- FastAPI
- LangChain
- FAISS
- Pydantic

## 🐛 Troubleshooting

### CORS Errors
- Ensure frontend and backend are running on correct ports
- Check CORS configuration in `Server/main.py`

### FAISS Index Issues
- Rebuild index: `python Services/utils/createDataBase.py`
- Verify index file exists: `Server/faiss_index/index.faiss`

### Module Import Errors
- Activate virtual environment
- Verify all dependencies: `pip install -r requirements.txt`

### Frontend Not Loading
- Clear browser cache
- Check Vite dev server is running
- Verify port 5173 is not in use

## 📚 Learning Resources

- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [React Documentation](https://react.dev/)
- [LangChain Documentation](https://python.langchain.com/)
- [FAISS Documentation](https://github.com/facebookresearch/faiss)
- [Vite Guide](https://vitejs.dev/)

## 🤝 Contributing

Contributions are welcome! Please:

1. Create a feature branch: `git checkout -b feature/YourFeature`
2. Commit changes: `git commit -m 'Add YourFeature'`
3. Push to branch: `git push origin feature/YourFeature`
4. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see LICENSE file for details.

## 📧 Contact & Support

For questions or support, please open an issue in the repository or contact the development team.

---

**Last Updated**: May 2026
**Version**: 1.0.0
