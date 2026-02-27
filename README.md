# AI Interview Evaluation & Scoring Engine

An advanced backend evaluation system built using FastAPI and OpenAI API to assess technical interview responses using structured scoring, anti-cheating detection, confidence calibration, plagiarism analysis, and multi-turn context tracking.

This project was implemented as part of an internship task focused on building a scalable and modular LLM-based evaluation system.

---

## 📌 Objective

To design and implement a comprehensive interview evaluation engine capable of:

- Weighted scoring rubric
- Anti-cheating detection
- Confidence-based score adjustment
- Plagiarism risk analysis
- Multi-turn interview context handling
- Risk engine output for integration

---

## 🏗 System Architecture Overview

The system follows a layered architecture:

```
Client → FastAPI (main.py)
        → Schema Validation (schemas.py)
        → Evaluation Layer (llm_evaluator.py)
            → Retry + Fallback Logic
            → JSON Enforcement
            → Anti-Cheat Detection
            → Confidence Adjustment
            → Plagiarism Detection
            → Context Tracking
        → Risk Engine Output
```

---

## ⚙️ Core Features

### 1️⃣ Weighted Scoring System
- Technical Accuracy (40%)
- Concept Clarity (25%)
- Keyword Coverage (20%)
- Communication (15%)

All scores are validated and normalized.

---

### 2️⃣ Retry + Fallback Mechanism
- Configurable retry attempts
- Exponential backoff
- Automatic fallback to mock mode if API quota fails
- Robust error handling

---

### 3️⃣ Anti-Cheating Detection
Heuristic detection of:
- Copy-paste indicators
- AI-generated phrasing
- Robotic responses
- Short / unnatural answers

Produces a confidence probability score.

---

### 4️⃣ Confidence Adjustment Engine
Uses:
- Whisper confidence
- Audio quality score
- Speech consistency
- Background noise level

Adjusts evaluation scores accordingly while preserving communication score integrity.

---

### 5️⃣ Plagiarism Detection Layer
- Semantic similarity checks
- Ideal answer comparison
- Risk categorization (Low / Medium / High / Critical)

---

### 6️⃣ Multi-Turn Context Tracking
- Maintains interview session state
- Tracks performance consistency
- Analyzes trend patterns
- Generates context influence insights

---

### 7️⃣ Risk Engine Output
Transforms evaluation result into:

- Cheat probability
- Risk flag
- Confidence level
- Quality metrics

Designed for integration with monitoring or ATS systems.

---

## 📂 Project Structure

```
gpt-llm-module-main/
│
├── app/
│   ├── main.py
│   ├── config.py
│   ├── schemas.py
│   ├── prompts/
│   └── services/
│
├── requirements.txt
├── .env.example
├── README.md
└── SYSTEM_ARCHITECTURE.md
```

---

## 🔧 Installation & Setup

1. Clone repository:

```
git clone https://github.com/YellankiKaushik/<repo-name>.git
cd <repo-name>
```

2. Create virtual environment:

```
python -m venv venv
venv\Scripts\activate
```

3. Install dependencies:

```
pip install -r requirements.txt
```

4. Create `.env` file based on `.env.example`:

```
OPENAI_API_KEY=your_api_key
USE_MOCK_MODE=false
```

5. Run server:

```
uvicorn app.main:app --reload
```

Access API Docs:
```
http://127.0.0.1:8000/docs
```

---

## 🧠 Design Decisions

- Modular service-based architecture for scalability
- Separation of prompt from business logic
- Config-driven retry + fallback handling
- Deterministic scoring using low temperature
- Risk engine abstraction for external integration
- Enhanced JSON enforcement to guarantee structure stability

---

## 🔄 Alternative Approaches Considered

- Single monolithic evaluator file (rejected for modular clarity)
- Pure rule-based scoring (rejected due to flexibility limitations)
- No fallback mode (rejected for robustness concerns)
- Static scoring without confidence adjustment (rejected for fairness)

---

## 📜 Conclusion

This system demonstrates:

- Backend architecture design
- LLM integration patterns
- Error handling & resilience
- Security awareness (env handling)
- Modular engineering principles
- Evaluation logic reasoning

Designed for clarity, explainability, and extensibility.