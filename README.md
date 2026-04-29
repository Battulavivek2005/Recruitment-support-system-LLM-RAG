An AI-powered recruitment platform that helps recruiters upload resumes, store candidate data, search for matching profiles, and review ranked results through a Streamlit dashboard.

Overview
This project combines:

A FastAPI backend for authentication, resume upload, search, and analytics
A Streamlit frontend for recruiter login and candidate discovery
Resume parsing and persistence for dataset and uploaded files
Embedding generation and Chroma vector storage for semantic search
RAG-based candidate retrieval with optional LLM-enhanced insights
Key Features
Admin-controlled user creation and user login
Bulk resume upload through API
Resume parsing for ingestion workflows
Candidate search by role, experience, and additional skills
Candidate ranking and recruiter-friendly result display
Resume detail viewing inside the frontend
Dashboard metrics for dataset coverage and retrieval quality
Vector database support for semantic candidate retrieval
Project Structure
ai_recruitment_system/
|-- backend/
|   |-- analytics/
|   |-- auth/
|   |-- database/
|   |-- embeddings/
|   |-- llm/
|   |-- rag/
|   |-- ranking/
|   |-- resume_processing/
|   |-- config.py
|   `-- main.py
|-- dataset/
|   |-- data/
|   `-- resume/
|-- frontend/
|   |-- candidate_search_ui.py
|   `-- dashboard.py
|-- vector_db/
|-- run_project.ps1
|-- requirements.txt
`-- README.md
Backend Modules
backend/main.py: FastAPI app entry point and API route definitions
backend/auth/: Authentication utilities and admin-controlled signup logic
backend/database/: Database connection, schema, and resume persistence
backend/resume_processing/: Resume parsing and upload workflows
backend/embeddings/: Embedding generation and vector-store integration
backend/rag/: Retrieval and candidate search pipeline
backend/llm/: LLM service integrations for enhanced recruiter insights
backend/analytics/: Project-level metrics and system evaluation
backend/ranking/: Candidate ranking helpers
Frontend
The Streamlit frontend provides:

Login screen for authorized users
Candidate search form
Filters for role, experience, and additional skills
Search result cards for matched candidates
Resume detail panel for selected profiles
Main frontend files:

frontend/dashboard.py
frontend/candidate_search_ui.py
API Endpoints
General
GET /
Health route that confirms the API is running.
Resume Upload
POST /upload_resume
Upload one or more resumes for parsing, database insertion, embedding generation, and vector indexing.
Search
GET /search
Basic RAG candidate search using a query string.

GET /search_llm
Candidate search with LLM-based recruiter insights when available.

POST /candidate_search
Structured recruiter search using role, experience, and additional_skills.

Analytics
GET /dashboard_metrics
Returns project and search-quality metrics.
Authentication
POST /auth/signup
Admin-only endpoint for creating users.

POST /auth/login
User login endpoint.

Technology Stack
Python
FastAPI
Uvicorn
Streamlit
Pandas
NumPy
Sentence Transformers
ChromaDB
Transformers
SQLAlchemy
OpenAI
pdfplumber
spaCy

Installation
1. Clone the project
git clone <your-repository-url>
cd ai_recruitment_system
2. Create and activate a virtual environment
python -m venv venv
.\venv\Scripts\Activate.ps1
3. Install dependencies
pip install -r requirements.txt

Running the Project
Use the following commands in PowerShell:
.\venv_clean\Scripts\activate
powershell -ExecutionPolicy Bypass -File .\run_project.ps1

This will:
- activate the project's Python virtual environment
- start the FastAPI backend
- start the Streamlit frontend
- open the project in your browser

This script:

selects venv_clean if available, otherwise venv
starts the FastAPI backend on 127.0.0.1:8002
starts the Streamlit frontend on 127.0.0.1:8501
opens the frontend in your browser
Manual Run Commands
Start backend
python -m uvicorn backend.main:app --host 127.0.0.1 --port 8002
Start frontend
python -m streamlit run frontend/dashboard.py --server.headless true --server.address 127.0.0.1 --server.port 8501
Data and Storage
Resume dataset files are stored under dataset/
Vector embeddings are persisted under vector_db/
SQLite database files are present in the project for resume and application data
Search Workflow
Resumes are collected from dataset files or uploads
Resume text is parsed and stored in the database
Embeddings are generated for each resume
Embeddings are stored in Chroma vector storage
Recruiters search by role, experience, and skills
Matching candidates are retrieved, ranked, and displayed
Optional LLM insights enhance result interpretation
Metrics and Evaluation
The analytics module computes metrics such as:

total resumes
dataset vs uploaded resume counts
category distribution
dataset synchronization percentage
supported format coverage
workflow completeness
retrieval quality metrics
overall system audit score
