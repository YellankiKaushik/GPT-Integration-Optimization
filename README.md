# AI Interview Evaluation & Scoring Engine

### GPT Integration Optimization Module

This repository contains the backend evaluation engine used in a **Domain-Based Intelligent Voice AI Interviewer** system.

The engine evaluates candidate responses during automated interviews using **LLM-based analysis, structured scoring, and reliability mechanisms**.

This implementation was developed as part of an internship task focused specifically on **optimizing GPT integration reliability and evaluation handling**.

---

# Project Objective

The goal of this module is to ensure that LLM-based interview evaluation remains:

* Reliable
* Structured
* Fault tolerant
* Easily integrable with other system components

This engine evaluates candidate answers and produces **structured evaluation results** that can be consumed by other modules such as:

* Interview controller
* Risk monitoring system
* Candidate scoring pipeline
* Interview summary generator

---

# Internship Task Scope

Assigned Module: **GPT Integration Optimization**

Primary responsibilities:

* Improve GPT API handling
* Ensure structured output reliability
* Implement retry logic
* Reduce system failure risk
* Handle API errors safely

The implementation focuses on **making LLM evaluation robust and production-ready**.

---

# System Architecture

```
Client Request
      │
      ▼
FastAPI Backend (main.py)
      │
      ▼
Schema Validation (schemas.py)
      │
      ▼
LLM Evaluation Engine (llm_evaluator.py)
      │
      ├── Retry Logic
      ├── GPT API Integration
      ├── JSON Enforcement
      ├── Anti-Cheating Detection
      ├── Confidence Adjustment
      ├── Plagiarism Analysis
      └── Context Tracking
      │
      ▼
Structured Evaluation Output
```

---

# Core Components

## 1. GPT Integration Layer

The **LLMEvaluator** class is responsible for interacting with the GPT API and generating evaluation results.

Responsibilities include:

* prompt preparation
* API request handling
* response parsing
* evaluation output generation

This layer acts as the **central intelligence engine** of the system.

---

## 2. Retry + Fallback Mechanism

LLM APIs may fail due to:

* rate limits
* network errors
* service interruptions

To ensure reliability the system implements:

* multiple retry attempts
* exponential backoff strategy
* automatic fallback evaluation

If the API fails repeatedly, the system safely switches to a **mock evaluation mode**, preventing system crashes.

---

## 3. Structured JSON Enforcement

LLMs can sometimes produce malformed responses.

To prevent downstream failures the system includes a **JSON validation layer** that:

* validates GPT responses
* repairs malformed JSON
* guarantees schema compliance

This ensures every response matches the required evaluation format.

---

## 4. Weighted Evaluation System

Candidate answers are evaluated using a weighted rubric:

| Metric             | Weight |
| ------------------ | ------ |
| Technical Accuracy | 40%    |
| Concept Clarity    | 25%    |
| Keyword Coverage   | 20%    |
| Communication      | 15%    |

The final score is calculated after validation and normalization.

---

## 5. Anti-Cheating Detection

The engine includes heuristics to identify suspicious responses such as:

* copy-paste indicators
* AI-generated phrasing
* robotic response patterns
* unusually short answers

The result includes a **risk confidence score**.

---

## 6. Confidence-Based Score Adjustment

Evaluation scores can be adjusted based on speech analysis signals such as:

* speech recognition confidence
* audio quality
* speech consistency
* background noise levels

This ensures fair scoring when audio quality affects transcription.

---

## 7. Multi-Turn Context Tracking

The system supports interview sessions with multiple questions.

It tracks:

* question history
* score progression
* keyword coverage trends
* consistency patterns

This enables **context-aware evaluation**.

---

# Example Evaluation Flow

```
Candidate Answer
      │
      ▼
FastAPI Endpoint
      │
      ▼
LLM Evaluation Engine
      │
      ▼
GPT API Call
      │
      ▼
Retry Logic + Error Handling
      │
      ▼
JSON Validation
      │
      ▼
Business Logic Validation
      │
      ▼
Final Structured Evaluation
```

---

# API Endpoints

| Endpoint                  | Description                        |
| ------------------------- | ---------------------------------- |
| `/evaluate/comprehensive` | Full evaluation pipeline           |
| `/evaluate/risk-engine`   | Output formatted for risk analysis |
| `/evaluate`               | Legacy compatibility endpoint      |
| `/evaluate/weights`       | Returns scoring weights            |
| `/evaluate/config`        | Returns system configuration       |

Swagger documentation:

```
http://127.0.0.1:8000/docs
```

---

# Installation

Clone repository:

```
git clone https://github.com/YellankiKaushik/GPT-Integration-Optimization.git
cd GPT-Integration-Optimization
```

Create virtual environment:

```
python -m venv venv
venv\Scripts\activate
```

Install dependencies:

```
pip install -r requirements.txt
```

Create environment configuration:

```
OPENAI_API_KEY=your_api_key
USE_MOCK_MODE=false
```

Run server:

```
uvicorn app.main:app --reload
```

Open API documentation:

```
http://127.0.0.1:8000/docs
```

---

# Key Design Principles

* Modular architecture
* Reliable LLM integration
* Fault-tolerant API communication
* Structured output validation
* Clear separation of concerns

These principles ensure the system can scale and integrate with larger interview platforms.

---

# Future Improvements

Possible improvements include:

* caching repeated evaluations
* streaming GPT responses
* domain-specific evaluation prompts
* improved semantic plagiarism detection
* distributed evaluation services

---

# Summary

This module demonstrates:

* reliable GPT API integration
* backend architecture design
* structured LLM evaluation pipelines
* fault-tolerant system design

The implementation focuses on **making LLM-based evaluation stable, predictable, and production-ready**.
