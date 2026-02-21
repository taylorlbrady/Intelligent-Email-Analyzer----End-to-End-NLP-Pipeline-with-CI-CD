# 📬 Intelligent Email Analyzer — End-to-End Build Plan

This document outlines the full development plan for building an end-to-end NLP system that classifies emails, routes them into folders, and extracts actionable tasks. The system includes data ingestion, preprocessing, model training, automation, API deployment, and CI/CD — all using free, open-source tools.

---

## 0. Project Setup
- Create GitHub repository with `README.md`, `.gitignore`, and `LICENSE`.
- Initialize Python project with `src/`, `tests/`, and `requirements.txt` or `pyproject.toml`.
- Define initial labels (e.g., work, finance, bills, travel, newsletters, urgent).
- Select integrations: Gmail API or IMAP for email; Todoist/Notion/Microsoft To Do for tasks.

---

## 1. Data Ingestion
- Connect to Gmail API, IMAP, or Microsoft Graph API.
- Fetch email metadata: sender, subject, body, timestamp.
- Store raw emails in SQLite/PostgreSQL or as JSONL files.
- Build a script to periodically pull new emails.

---

## 2. Dataset Creation & Labeling
- Collect 300–1000 emails (personal, synthetic, or forwarded).
- Manually label emails into predefined categories.
- Save dataset with fields: `email_id`, `subject`, `body`, `labels`.

---

## 3. Preprocessing & Feature Engineering
- Clean HTML, signatures, and quoted replies using BeautifulSoup and regex.
- Normalize text and combine subject + body.
- Generate embeddings using Sentence Transformers (e.g., `all-MiniLM-L6-v2`).
- Store embeddings for model training.

---

## 4. Model Development
- Train a multi-label classifier using scikit-learn or PyTorch.
- Evaluate using F1-score, precision/recall, and confusion matrices.
- Iterate on preprocessing and label definitions as needed.
- Package model into a `ModelService` class with `load_model()` and `predict()`.

---

## 5. Task Extraction Module
- Define actionable task patterns (e.g., pay bill, schedule meeting).
- Implement rule-based extraction using spaCy, regex, and dateparser.
- Optionally integrate a local LLM (Llama/Mistral via Ollama) for structured extraction.
- Output structured tasks with descriptions and due dates.

---

## 6. Automation Layer
- Map classification labels to email folders.
- Implement folder movement using Gmail API or IMAP.
- Integrate with Todoist/Notion/Microsoft To Do to create tasks.
- Build an orchestrator: classify → extract tasks → move email → create tasks.

---

## 7. API Service
- Build a FastAPI application with endpoints:
  - `POST /analyze-email`
  - `GET /health`
- Use Pydantic models for request/response validation.
- Add OpenAPI documentation via FastAPI’s auto-generated docs.

---

## 8. Containerization
- Create a Dockerfile using `python:3.11-slim`.
- Install dependencies and copy project files.
- Expose API via Uvicorn.
- Test locally with Docker Compose if needed.

---

## 9. CI/CD Pipeline
- Use GitHub Actions for:
  - Linting (ruff/flake8)
  - Unit tests (pytest)
  - Building Docker images
  - Pushing images to GitHub Container Registry
  - Deploying to Render/Railway/Fly.io (free tiers)
- Add model versioning using MLflow or DVC.

---

## 10. Monitoring & Maintenance
- Log predictions, actions, and errors.
- Track model drift and misclassifications.
- Build dashboards using Prometheus + Grafana (optional).
- Add periodic retraining workflow using Prefect or cron jobs.

---

## 11. Future Enhancements
- Add zero-shot classification fallback.
- Improve task extraction with fine-tuned LLMs.
- Add user feedback loop for correcting labels.
- Build a simple web UI for reviewing processed emails.

---
