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
  project-c-agentic-maestro/     # Weeks 10–12 (placeholder)
```

## Week 1 — Toy chat + trust boundaries

Minimal FastAPI chat that calls an OpenAI-compatible LLM (Groq free tier by default). No auth. Stub replies if no key is set.

### Quick start (free Groq)

1. Get a free API key at [console.groq.com/keys](https://console.groq.com/keys) (do **not** paste it into chat).
2. Copy the example env file and put the key only in `.env` (gitignored):

```bash
cd project-a-prompt-security/week1/app
cp .env.example .env
# edit .env — set LLM_API_KEY=...  (GROQ_API_KEY also works)
```

3. Install deps and run:

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

4. In another terminal, run the five NOTES probes:

```bash
cd project-a-prompt-security/week1
python run_probes.py
```

Optional env vars (defaults target Groq free tier): `LLM_BASE_URL`, `LLM_MODEL`.  
Without a key, `/chat` stays in stub mode (`llm_configured: false`).

Scratch probes + results: [project-a-prompt-security/week1/NOTES.md](project-a-prompt-security/week1/NOTES.md).

## Next step (Joshua)

1. Set `LLM_API_KEY` in `week1/app/.env` (or as a Cursor cloud secret named `LLM_API_KEY` / `GROQ_API_KEY`).
2. Re-run `python run_probes.py` and fill Result/Evidence in `NOTES.md`.
3. Week 2: turn this into the Company FAQ Assistant and map trust boundaries.
