# AI Security Portfolio

Hands-on AI security assessments for **Joshua Sitompul** — build, break safely, fix, and document.

**Goal:** Assessment-grade portfolio (findings, risk register, controls, residual risk), not certs or demos.  
**Budget:** Free preferred; hard cap ~$20 — see [BUDGET.md](BUDGET.md).  
**Plan:** 90-day path — Project A (prompt security) → B (RAG) → C (agentic / MAESTRO).

## Layout

```text
ai-security-portfolio/
  BUDGET.md
  templates/                      # finding, risk register, assessment report
  project-a-prompt-security/      # Weeks 2–5 (Week 1 warm-up lives here)
  project-b-rag-security/         # Weeks 6–9 (placeholder)
  project-c-agentic-maestro/      # Weeks 10–12 (placeholder)
```

## Week 1 — Toy chat + trust boundaries

Minimal FastAPI chat that calls an OpenAI-compatible LLM (Groq, OpenAI, etc.) via env vars. No auth. Stub replies if no key is set.

```bash
cd project-a-prompt-security/week1/app
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt

# Optional — live LLM (Groq free tier works):
export LLM_API_KEY="gsk_..."
export LLM_BASE_URL="https://api.groq.com/openai/v1"   # default
export LLM_MODEL="llama-3.1-8b-instant"                # default

uvicorn main:app --reload --port 8000
# POST http://127.0.0.1:8000/chat  {"message": "hello"}
# GET  http://127.0.0.1:8000/health
```

Scratch probes: [project-a-prompt-security/week1/NOTES.md](project-a-prompt-security/week1/NOTES.md).

## Next step (Joshua)

1. Set `LLM_API_KEY` (Groq free tier recommended).
2. Re-run the five probes in `NOTES.md` against a live model; fill Pass/Fail + evidence.
3. Week 2: turn this into the Company FAQ Assistant and map trust boundaries.
