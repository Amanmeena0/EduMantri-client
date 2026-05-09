# EduMantri (VAHEI 2.0)

EduMantri is a comprehensive RAG-based (Retrieval-Augmented Generation) application designed to provide intelligent chatbot interactions. It features a scalable backend built with FastAPI and a modern frontend powered by React.

---

# 🚀 Features

- Intelligent RAG-based conversational AI
- FastAPI-powered backend APIs
- LangChain-based retrieval pipeline
- Vector search using Qdrant
- Queue management with Redis + Celery
- Object storage using MinIO
- PostgreSQL metadata storage
- Interactive React frontend
- Responsive UI with Tailwind CSS and Material UI
- Speech Recognition and Text-to-Speech support
- Session management and debugging commands
- CORS-enabled backend integration

---

# 🏗️ System Architecture

The platform uses a modern distributed architecture for scalable AI applications.

## Core Components

| Component | Technology |
|---|---|
| API Backend | FastAPI |
| Queue Management | Redis + Celery |
| Object Storage | MinIO |
| Vector Database | Qdrant |
| Metadata Storage | PostgreSQL |
| Frontend | React 19 + Vite |
| RAG Framework | LangChain |
| LLM Integration | Google GenAI + Transformers |

---

# 🛠️ Tech Stack

## Backend

- FastAPI
- LangChain
- Google Generative AI
- Transformers
- Pydantic
- Python Dotenv
- Tenacity
- Redis
- Celery
- Qdrant
- PostgreSQL
- MinIO
- pyttsx3
- SpeechRecognition

## Frontend

- React 19
- Vite
- Tailwind CSS 4
- Material UI (MUI)
- Emotion

---

# 📂 Project Structure

```bash
EduMantri/
│
├── server/                 # FastAPI backend
│   ├── main.py
│   ├── routes/
│   ├── services/
│   ├── rag/
│   ├── models/
│   └── requirements.txt
│
├── my-react-app/           # React frontend
│   ├── src/
│   ├── public/
│   └── package.json
│
└── README.md
```

---

# ⚙️ Installation

## 1. Clone the Repository

```bash
git clone <your-repository-url>
cd EduMantri
```

---

# 🔧 Backend Setup

## Navigate to the Backend Directory

```bash
cd server
```

## Create Virtual Environment

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

## Install Dependencies

```bash
pip install -r requirements.txt
```

## Start the FastAPI Server

```bash
python main.py
```

Backend will run on:

```bash
http://localhost:8000
```

---

# 💻 Frontend Setup

## Navigate to Frontend Directory

```bash
cd my-react-app
```

## Install Dependencies

```bash
npm install
```

## Start Development Server

```bash
npm run dev
```

Frontend will run on:

```bash
http://localhost:5173
```

---

# 🔌 API Endpoints

## POST `/chat`

Handles chatbot interactions.

### Request Body

```json
{
  "query": "What is Retrieval-Augmented Generation?"
}
```

### Response

```json
{
  "response": "Retrieval-Augmented Generation (RAG) is...",
  "follow_up_questions": [
    "How does RAG work?",
    "What are vector databases?"
  ]
}
```

---

## GET `/health`

Returns backend health status.

### Response

```json
{
  "status": "healthy"
}
```

---

# 🧠 RAG Pipeline

The system uses a Retrieval-Augmented Generation workflow:

1. User submits a query
2. Query embeddings are generated
3. Relevant documents are retrieved from Qdrant
4. LangChain processes contextual retrieval
5. LLM generates context-aware responses
6. Response is returned to frontend

---

# 🎨 Frontend Features

- Real-time chatbot interface
- Responsive UI design
- Material UI components
- Tailwind CSS styling
- Speech-to-Text support
- Text-to-Speech responses
- Session management commands
- Suggested follow-up questions

---

# 🔐 Environment Variables

Create a `.env` file inside the `server/` directory.

```env
GOOGLE_API_KEY=your_api_key
QDRANT_URL=your_qdrant_url
QDRANT_API_KEY=your_qdrant_api_key
POSTGRES_URL=your_postgres_url
MINIO_ENDPOINT=your_minio_endpoint
REDIS_URL=your_redis_url
```

---

# 📦 Future Improvements

- Authentication & Authorization
- Multi-user chat sessions
- Conversation memory
- Streaming responses
- Document upload support
- Admin dashboard
- Docker deployment
- Kubernetes orchestration
- CI/CD pipeline integration

---

# 👨‍💻 Development Commands

## Backend

```bash
python main.py
```

## Frontend

```bash
npm run dev
```

## Build Frontend

```bash
npm run build
```

---

# 📄 License

This project is licensed under the MIT License.

---

# 🙌 Contributors

Developed by Aman Meena

```
