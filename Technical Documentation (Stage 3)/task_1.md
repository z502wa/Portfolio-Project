## Task 1: Design System Architecture

### High-Level Overview
The MVP is a web application that generates a concise, source-backed travel plan using an AI model and web search enrichment. It runs as a stateless front end (Streamlit) with no persistent database in the MVP. External services include Groq (LLM) and SerpAPI (web search). Session data is kept in memory.

---

### Components
- **Frontend (Streamlit Web App)**
  - UI for inputs: Destination, Duration, Budget (Budget/Moderate/Luxury), Travel Styles (multi-select), Answer Language.
  - Actions: “Generate Plan”, Q&A (expander), Export to PDF.
  - Holds ephemeral state in `st.session_state` (e.g., generated plan).

- **Prompt Builder (in-app)**
  - Transforms user inputs into a structured prompt (instructions + constraints).
  - Controls output length/format (Markdown ~600 words) and requires source links.

- **LLM Service**
  - **Groq (Llama)** via API.
  - Returns the initial plan: best time to visit, day-by-day itinerary, budget-aware stays, culinary highlights, practical & safety tips, estimated total cost.

- **Search/Enrichment Service**
  - **SerpAPI** (Google Search / Maps / Hotels endpoints as needed).
  - Fetches verifiable links, updated hotel/attraction details, and supporting references to enrich/validate the AI output.

- **Plan Post-Processor (in-app)**
  - Normalizes/merges AI text with SerpAPI results (e.g., add links/titles, ensure sections exist).
  - Produces final Markdown for rendering and export.

- **PDF Exporter (in-app)**
  - Converts the rendered Markdown plan to a downloadable PDF.

- **(Optional / Future) Persistence**
  - Not part of MVP. If needed later: SQLite/PostgreSQL for saved plans and analytics.

---

### Data Flow Diagram

![System Architecture Diagram](https://github.com/z502wa/Portfolio-Project/blob/main/Technical%20Documentation%20(Stage%203)/data_flow_diagram.png)

---

### Request/Response Paths
1. **Generate Plan**
   - FE → Prompt Builder → LLM → SerpAPI → Post-Processor → FE (render Markdown) → PDF (on demand).

2. **Q&A**
   - FE (question) → Q&A Handler (injects plan context) → LLM → FE (render answer).

---

### Notes on Scalability & Efficiency
- **Stateless UI** for the MVP; state is session-only. Horizontal scaling is straightforward if needed (behind a reverse proxy).
- **Rate limits & resilience**
  - Cache SerpAPI queries (short TTL) where possible.
  - Graceful fallbacks (reduced results or static examples) on external failure.
- **Security & Secrets**
  - Keep API keys in environment/secrets (no client exposure).
  - Validate/escape user inputs; never render untrusted HTML.
- **Performance**
  - Constrain LLM output length and sections.
  - Defer enrichment (SerpAPI) to only required sections.
- **Internationalization**
  - Language toggle drives prompt instructions and UI text; content generation remains deterministic per language.

---

### Technology Choices (MVP)
- **Frontend:** Streamlit (fast iteration, simple state handling).
- **LLM:** Groq (Llama) via API for plan generation & Q&A.
- **Search:** SerpAPI for reliable, structured web results and links.
- **PDF:** Markdown → PDF converter (tooling within app environment).
- **Database:** None for MVP (future: SQLite/PostgreSQL if persistence is required).

---

### Deliverable
- **Diagram illustrating the architecture and data flow** (linked above).
- **Accompanying description** of each component and integration points.
