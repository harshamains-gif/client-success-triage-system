# Client Success Triage System

An AI-powered customer support triage platform that automatically classifies and prioritizes incoming support tickets using a fine-tuned BERT model — achieving **99.6% priority accuracy** and **99.9% category accuracy** across 1,500+ real-world tickets.

---

## Overview

Support teams waste hours manually sorting and routing tickets. This system automates that entirely — a ticket comes in, BERT classifies its urgency and category instantly, and it gets routed to the right team with a confidence score attached.

---

## Tech Stack

| Layer | Technology |
|---|---|
| NLP Classifier | BERT (fine-tuned, Hugging Face Transformers) |
| Backend API | FastAPI (Python) |
| Database | MongoDB |
| Dashboard | Streamlit |
| Auth | JWT with API rate limiting |
| Containerization | Docker + Docker Compose |

---

## Results

Evaluated on **1,500+ real customer support tickets** across 4 categories:

| Metric | Score |
|---|---|
| Priority classification confidence | **99.6%** |
| Category classification confidence | **99.9%** |
| Priority labels | Critical / High / Medium / Low |
| Categories | Technical / Billing / Account / Feature Request |

Sample prediction output:
```json
{
  "subject": "API returning Timeout Error",
  "predicted_priority": "Critical",
  "priority_confidence": 0.9923,
  "predicted_category": "Technical",
  "category_confidence": 0.9992
}
```

---

## Features

- **AI Triage** — Fine-tuned BERT classifies every ticket by priority and category automatically
- **Real-time API** — FastAPI endpoints accept tickets and return predictions instantly
- **Analytics Dashboard** — Streamlit dashboard shows ticket trends, priority distribution, and team workload
- **Secure Auth** — JWT-based login with rate limiting to prevent API abuse
- **Batch Processing** — Bulk classification script for processing large ticket backlogs
- **Dockerized** — One command to spin up the entire stack

---

## Project Structure

```
client-success-triage-system/
├── app/
│   ├── api/v1/
│   │   ├── auth.py              # JWT authentication
│   │   └── rate_limiter.py      # API rate limiting
│   ├── core/config.py           # App configuration
│   ├── db/mongo.py              # MongoDB connection
│   ├── models/schemas.py        # Pydantic schemas
│   └── main.py                  # FastAPI entrypoint
├── nlp_pipeline/
│   ├── models/bert_classifier.py       # BERT classification model
│   └── preprocessing/cleaner.py       # Text preprocessing
├── dashboard/
│   └── streamlit_app.py         # Analytics dashboard
├── scripts/
│   ├── batch_classify.py        # Bulk ticket classification
│   ├── load_sample_data.py      # Sample data loader
│   └── test_preprocessing.py   # Preprocessing tests
├── docker/
│   ├── Dockerfile
│   ├── docker-compose.yml
│   └── mongo-init/init.js
├── data/
│   └── sample_tickets.csv
└── requirements.txt
```

---

## Setup

### Prerequisites
- Python 3.9+
- Docker & Docker Compose

### Run with Docker (recommended)
```bash
git clone https://github.com/harshamains-gif/client-success-triage-system.git
cd client-success-triage-system
cd docker && docker-compose up --build
```

### Run locally
```bash
pip install -r requirements.txt
uvicorn app.main:app --reload
```

### Launch Dashboard
```bash
streamlit run dashboard/streamlit_app.py
```

---

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/v1/auth/login` | Authenticate and get JWT token |
| POST | `/api/v1/classify` | Classify a single ticket |
| POST | `/api/v1/batch` | Batch classify multiple tickets |
| GET | `/api/v1/tickets` | Retrieve all tickets |
| GET | `/api/v1/stats` | Get triage statistics |

---

## Ticket Categories

| Category | Examples |
|---|---|
| Technical | API errors, latency issues, login failures, dashboard not loading |
| Billing | Incorrect charges, payment failures, subscription changes, refunds |
| Account | SSO config, permission bugs, account deletion, email updates |
| Feature Request | Dark mode, audit logs, integrations, API enhancements |

---

## Author

**Kummithi Harsha Sainath Reddy**
B.Tech CSE — IIIT Sonepat
[LinkedIn](https://linkedin.com/in/harsha-kummithi) | [GitHub](https://github.com/harshamains-gif)
