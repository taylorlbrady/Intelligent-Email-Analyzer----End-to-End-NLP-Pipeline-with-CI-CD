# Intelligent-Email-Analyzer----End-to-End-NLP-Pipeline-with-CI-CD
End‑to‑end NLP system that classifies emails, routes them to folders, and extracts actionable tasks. Includes data ingestion, preprocessing, ML model training, FastAPI service, Docker deployment, and CI/CD with GitHub Actions using only free, open‑source tools.

---

## (Planned) Features

- **Email Classification**  
  Categorizes emails (work, finance, bills, travel, newsletters, urgent, etc.) using Sentence Transformer embeddings and a multi-label classifier.

- **Task Extraction**  
  Identifies actionable items (e.g., pay bill, schedule meeting) using rule-based NLP and optional local LLM inference.

- **Automated Workflow**  
  Integrates with Gmail API and Todoist/Notion/Microsoft To Do to move emails into folders and create tasks automatically.

- **FastAPI Microservice**  
  Provides a clean REST API for email analysis, packaged in a Dockerized service.

- **CI/CD Pipeline**  
  GitHub Actions handles linting, testing, Docker builds, and deployment to a free cloud platform.

- **MLOps Components**  
  Includes dataset/model versioning (DVC/MLflow) and optional monitoring (Prometheus/Grafana).

---

## (Planned) Tech Stack

**Languages & Libraries**  
- Python, FastAPI, scikit-learn, PyTorch  
- Sentence Transformers, spaCy, BeautifulSoup, regex  

**Infrastructure & Deployment**  
- Docker, GitHub Actions  
- Render / Railway / Fly.io (free tiers)

**MLOps**  
- MLflow or DVC  
- Prometheus + Grafana (optional)

---

## 📐 Project Structure (Planned)
