# Full-Stack Roadmap for a Data Science Role (Tailored)

> **Designed around your situation**
> - Python: comfortable, has done small DS projects (a real strength)
> - Web / DB / backend / frontend: no experience (start from basics)
> - Study time: 20–30 hrs/week
> - Target window: 6–12 months → **36-week (~8 month) core + remaining time for capstone polish & job search buffer**

No compression. With enough time available, the strategy is "solid fundamentals + one product built deeply", not "wide and shallow". The Python base means the backend is absorbed fast; web/DB are blank slates, so more time is allocated there.

---

## Big Picture (36 weeks)

| Phase | Weeks | Topic | Key deliverable |
|---|---|---|---|
| 0 | 1–3 | Dev & web fundamentals | Git workflow + clean repo |
| 1 | 4–9 | Backend & API (FastAPI) | REST API with auth |
| 2 | 10–16 | DB & storage (SQL/Supabase/S3) | Backend wired to DB & storage |
| 3 | 17–24 | Frontend (JS → React → Next.js) | Web app connected to API |
| 4 | 25–29 | ML model serving integration | Full-stack app with a model in it |
| 5 | 30–36 | MLOps & cloud deployment | Deployed, monitored product |
| Capstone | parallel from Week 25 | Portfolio project | End-to-end ML service for hiring |

At 20–30 hrs/week, each week includes "theory + hands-on coding + a small deliverable". **Weeks where you get stuck will definitely happen**, so the last week of each phase is deliberately left as an integration/review week.

---

## Phase 0 — Dev & Web Fundamentals (Weeks 1–3)

Web/backend/frontend are all new, so Phase 0 is extended from 2 to **3 weeks**. Locking in a solid mental model of "how the web works" here determines the speed of everything after.

Learning content:
- Git/GitHub: branch, PR, merge, rebase, `.gitignore`, commit conventions
- Terminal/shell: paths, environment variables, processes, sending requests with `curl`
- Python env management: `uv` for dependency locking & virtual envs (more modern than older approaches)
- **How the web works (essential since blank slate)**: client-server, DNS, HTTP request/response, methods, status codes, headers, JSON, how a browser renders a page
- Docker concepts: image vs container, `Dockerfile`, `docker run` (usage in Phase 5, concepts now)

Recommended resources:
- Git: "Pro Git" chapters 1–3 (free)
- How the web works: MDN "How the web works" + "An overview of HTTP"
- Docker: official "Get Started"

Deliverables:
- Turn one existing DS notebook into a clean GitHub repo with `uv` env + README + `.gitignore`
- Be able to call a public API (e.g. GitHub API) with `curl` and explain the response structure

> Week 3 is a review/consolidation week. Re-clarify anything fuzzy before moving on. Wobbling here slows down Phases 1–3 entirely.

---

## Phase 1 — Backend & API (Weeks 4–9)

**The phase that leverages your biggest strength.** Because you know Python, FastAPI is absorbed fast. 6 weeks are allocated to make the backend a genuine weapon.

Learning content:
- FastAPI: routing, path/query/body parameters
- Pydantic: request/response schema validation, type modeling
- async/await basics (concept level)
- Dependency injection (Depends), middleware, exception handling
- Auth/authz: password hashing, JWT tokens, OAuth2 flow concept
- Testing: `pytest` + `httpx`; verify with Swagger UI / Postman / `curl`
- API design principles: RESTful resource naming, pagination, versioning, standard error responses

Week by week:
- Week 4: FastAPI basics + Pydantic, in-memory CRUD API
- Week 5: async concept, dependency injection, middleware, structured error handling
- Week 6: Auth — signup/login, password hashing, JWT issue/verify
- Week 7: API tests with `pytest`, edge case handling
- Week 8: Mini project — "dataset metadata management API" (tags, search, pagination)
- Week 9: Refactor / document / review week

Recommended resources:
- FastAPI official tutorial (thorough; follow it start to finish)
- Auth: FastAPI official "Security" section

Deliverable:
- One REST API repo with auth + tests + auto docs

---

## Phase 2 — DB & Storage (Weeks 10–16)

DB experience is zero, so this is the longest at 7 weeks. In a data science role, **being able to handle an operational DB** is a strong differentiator (analytics SQL and operational SQL differ).

Core concept — start with role separation:
- **PostgreSQL / Supabase**: structured data (users, prediction logs, metadata)
- **S3 / Supabase Storage / Cloudflare R2**: unstructured large files (model artifacts, datasets, images)

Learning content:
- Relational DB: schema design, normalization, primary/foreign keys, indexes, transactions, JOINs
- Difference between operational SQL and analytics SQL (you've likely only done the analytics side)
- ORM: SQLModel (made by FastAPI's author, Pydantic-integrated → gentle learning curve)
- Migrations: Alembic
- Supabase: project creation, Postgres connection, Auth, Row Level Security (RLS), Python client
- S3/R2: bucket/object concepts, presigned URLs (safe upload/download without server load), `boto3`
- Secret management: `.env`, environment variables, never commit keys

Week by week:
- Week 10: SQL fundamentals (separate week since blank slate) — DDL/DML, JOIN, indexes
- Week 11: Connect Phase 1 API to a real Postgres via SQLModel
- Week 12: Schema design practice + Alembic migrations
- Week 13: Migrate to Supabase, use built-in Auth
- Week 14: Apply Row Level Security (multi-user data isolation)
- Week 15: Storage integration — file upload/download, presigned URLs
- Week 16: Integration — "CSV upload → file to storage, metadata to DB" + review week

Recommended resources:
- SQL: "SQLBolt" or "Mode SQL Tutorial" (interactive, fast)
- SQLModel official tutorial
- Supabase official "Quickstart" + "Auth" + "Row Level Security"
- Presigned URLs: AWS `boto3` official guide section

Cost tip: for learning, prefer **Cloudflare R2 (free egress)** or Supabase Storage over AWS S3. They're S3-compatible APIs, so switching later costs almost nothing.

Deliverable:
- Backend integrating DB + object storage + multi-user auth (the ML service's data layer is complete)

---

## Phase 3 — Frontend (Weeks 17–24)

Zero frontend experience + the phase DS people find hardest, so it's the longest at 8 weeks, staged gradually. **The goal is not "designer level" but "I can build a screen that shows my model's results myself".** Holding that line makes 8 weeks enough.

Learning content:
- HTML/CSS, essentials only: box model, Flexbox/Grid, basic responsiveness
- JavaScript (ES6+): variables, functions, array methods, `fetch`, `async/await`, modules, destructuring (knowing Python makes the syntax fast to absorb)
- React: components, props, state (`useState`), `useEffect`, list rendering, forms, conditional rendering
- API integration: calling the backend, handling loading/error/empty states
- Next.js: routing, server/client component concepts, API routes
- Tailwind CSS: building presentable UI fast
- Data visualization: Recharts or Plotly.js (directly useful for DS result visualization)

Week by week:
- Week 17: HTML/CSS basics (layout-focused, not design depth)
- Week 18: JavaScript core syntax + calling APIs with `fetch`
- Week 19: React basics — components and state
- Week 20: React `useEffect` + API integration, state handling
- Week 21: Switch to Next.js + routing + Tailwind styling
- Week 22: Form handling — connect login/input forms to the Phase 2 backend
- Week 23: Chart/dashboard screen (prediction result visualization)
- Week 24: Complete a front+back integrated mini app + review week

Recommended resources:
- JavaScript: javascript.info
- React: official "Learn React" (react.dev)
- Next.js: official "Learn" course
- Tailwind: official docs + component examples

Shortcut option (optional): if time pressure is high, build the capstone MVP first with **Streamlit/Gradio**, then rebuild on top with React/Next.js. But to be credited with "full-stack experience", keep at least one React project.

Deliverable:
- A web app connected to the backend API that shows data/charts

---

## Phase 4 — ML Model Serving Integration (Weeks 25–29)

The phase that adds your DS color. **From here, work in parallel with the capstone project** (see capstone section).

Learning content:
- Model serialization: `joblib`/`pickle`, model versioning
- Inference API design: input validation, sync/async prediction, batch prediction, timeouts
- Pattern: store model artifact in S3/R2, load it at API startup
- Inference performance: latency, model load optimization, caching
- Prediction logging: record input/output/latency in the DB (basis for retraining & monitoring)
- Frontend connection: input → prediction → result visualization flow complete

Week by week:
- Week 25: Serve a trained model as a FastAPI endpoint + finalize capstone topic
- Week 26: Load model artifact from S3/R2, log predictions to DB
- Week 27: Connect frontend — user input → prediction → visualization
- Week 28: Input validation / error handling / edge cases
- Week 29: Capstone MVP complete + review week

Deliverable:
- A full-stack ML app where "input → model inference → result display + logging" works

---

## Phase 5 — MLOps & Cloud Deployment (Weeks 30–36)

**The phase that most strongly differentiates a DS candidate in the job market.** Most people stop at the model. Going this far puts you in the top tier.

Learning content:
- Containerization: multi-stage Dockerfile, `docker-compose` for local API+DB
- CI/CD: GitHub Actions — automated tests, image build, auto deploy
- Experiment tracking: MLflow or Weights & Biases — log params/metrics/artifacts
- Model registry concept: versioning, staging, promotion to production
- Pipeline orchestration: Prefect (easy entry) — automate collect→preprocess→train→evaluate
- Monitoring: data/model drift detection (Evidently), basic logging/alerts
- Cloud deployment: start with Render/Railway/Fly.io → expand to AWS when ready
- Ops concepts: env separation (dev/prod), secret management, health checks

Week by week:
- Week 30: Containerize the whole app with Docker + docker-compose
- Week 31: Automate test+build with GitHub Actions
- Week 32: Cloud deploy — secure a public URL (the core of the portfolio)
- Week 33: MLflow experiment tracking + model registry
- Week 34: Build a retraining pipeline with Prefect
- Week 35: Drift monitoring with Evidently
- Week 36: Full documentation + architecture diagram + finalize README + review week

Recommended resources:
- Made With ML (madewithml.com) — free MLOps course, ideal for the DS→production flow
- MLflow / Prefect / Evidently official quickstarts
- GitHub Actions official docs

Deliverable:
- An ML service reachable at a public URL with CI/CD + experiment tracking + monitoring attached

---

## Capstone Project (parallel from Week 25, polished after Week 36)

The single key artifact you show in interviews. Invest the time after Week 36 (within the 6–12 month window) here — completeness decides the outcome.

Requirements:
- Real data from a domain you care about (not a trivial Kaggle classification; ideally self-collected / public API)
- End-to-end: collect → store (S3/DB) → train → serve (API) → UI → deploy → monitor
- README: architecture diagram, reasons behind decisions, limitations, improvement plan
- Live demo URL + clean GitHub

Direction examples:
- Domain prediction service (price/demand/churn) + dashboard + periodic retraining
- Text/image classification API + user feedback collection → data flywheel
- Public data pipeline + anomaly detection + alerts

---

## Three Key Pieces of Advice for Your Situation

1. **Leverage the Python strength**: Phase 1 (backend) is what you'll absorb fastest. Build confidence there, and use that energy to push through the blank-slate frontend (Phase 3).
2. **Don't take the DB lightly**: even if you've done analytics SQL, operational DB design / indexes / transactions / RLS are different. That's why Phase 2 gets 7 weeks — and interviews probe this area more deeply than expected.
3. **Plenty of time can be a trap**: 6–12 months looks long, but full-stack + MLOps from scratch is tight. Never lose the rhythm of pushing a small artifact to GitHub every week. Committed output, not study hours, is the true measure of progress.

---

## Self-Check Checklist (before interviews)

- [ ] Can design a REST API and add auth (JWT)
- [ ] Can design a Postgres schema and use an ORM (SQLModel)
- [ ] Can explain the difference between operational SQL and analytics SQL
- [ ] Can safely upload/download files to S3/R2 (can explain presigned URLs)
- [ ] Can build a screen connected to an API with React/Next.js
- [ ] Can serve a model as an API and log predictions
- [ ] Can containerize with Docker and deploy to the cloud
- [ ] Can set up CI/CD with GitHub Actions
- [ ] Have applied experiment tracking & drift monitoring
- [ ] Have one live demo project containing all of the above
