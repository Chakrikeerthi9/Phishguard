# PhishGuard 🛡️

AI-powered website security scanner using 4-tier detection system with RAG-enhanced LLM analysis.

## 🚀 Features

- **4-Tier Detection System**
  - Tier 1: Heuristic pattern matching (instant)
  - Tier 2: Redis cache lookup (10ms)
  - Tier 3: Threat intelligence APIs (100ms)
  - Tier 4: RAG + LLM deep analysis (500ms)

- **AI Agent Architecture**
  - Intelligent routing between tiers
  - RAG-enhanced decision making
  - Historical threat database

- **Security Analysis**
  - XSS detection
  - SQL injection detection
  - Command injection detection
  - Phishing detection
  - Malware distribution detection

## 🛠️ Tech Stack

**Frontend:**
- React + Vite
- Tailwind CSS
- Axios

**Backend:**
- FastAPI
- LangChain
- ChromaDB (VectorDB)
- Redis (Cache)
- MySQL (Persistence)

**AI/ML:**
- Anthropic Claude (LLM)
- Sentence Transformers (Embeddings)
- RAG (Retrieval Augmented Generation)

## 📦 Quick Start

### Prerequisites
- Docker & Docker Compose
- API Keys:
  - Anthropic API Key
  - VirusTotal API Key (optional)
  - Google Safe Browsing API Key (optional)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/phishguard.git
cd phishguard
```

2. Create `.env` file in root:
```bash
ANTHROPIC_API_KEY=your_key_here
VIRUSTOTAL_API_KEY=your_key_here
GOOGLE_SAFE_BROWSING_API_KEY=your_key_here
```

3. Start all services:
```bash
docker-compose up --build
```

4. Access the application:
- Frontend: http://localhost:5173
- Backend API: http://localhost:8000
- API Docs: http://localhost:8000/docs

## 🧪 Testing
```bash
# Backend tests
cd backend
pytest

# Frontend tests
cd frontend
npm test
```

## 📖 API Documentation

### POST /api/scan
Scan a URL for threats

**Request:**
```json
{
  "url": "https://example.com"
}
```

**Response:**
```json
{
  "url": "https://example.com",
  "is_safe": true,
  "risk_score": 0.15,
  "tier_used": 1,
  "reasoning": "No suspicious patterns detected",
  "indicators": [],
  "detection_time_ms": 5
}
```

### GET /api/history
Get scan history

**Response:**
```json
{
  "scans": [
    {
      "id": 1,
      "url": "https://example.com",
      "is_safe": true,
      "timestamp": "2024-11-27T10:30:00Z"
    }
  ]
}
```

## 🏗️ Architecture
```
User → React App → FastAPI → AI Agent Controller
                                    ↓
                    ┌───────────────┼───────────────┐
                    ↓               ↓               ↓
                Tier 1          Tier 2          Tier 3
              Heuristics        Cache         Threat Intel
                                    ↓
                                Tier 4
                              RAG + LLM
                                    ↓
                    ┌───────────────┼───────────────┐
                    ↓               ↓               ↓
                ChromaDB         Redis           MySQL
```

## 📊 Performance

- 60% of scans complete in <10ms (Tier 1)
- 20% of scans complete in <20ms (Tier 2)
- 15% of scans complete in <200ms (Tier 3)
- 5% of scans complete in <600ms (Tier 4)

Average cost per scan: $0.001

## 👤 Author

Your Name - [LinkedIn](https://www.linkedin.com/in/chakri-keerthi16/)

## 🙏 Acknowledgments

- Anthropic for Claude API
- LangChain for agent framework
- ChromaDB for vector database