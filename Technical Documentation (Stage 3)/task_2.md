
## Task 2: Define Components, Classes, and Database Design

### 0) Design Rationale (MVP – Front-End Only)
This MVP intentionally ships **without a dedicated back-end or database**.  
All state is **ephemeral and stored in-memory** on the client app (session state), and external services are used for computation and data enrichment.  
This minimizes complexity, speeds up delivery, and fully satisfies current functional requirements.

---

### 1) Logical Components (No Server Back-End)
- **UI Layer (Streamlit App)**
  - Collects inputs: Destination, Duration, Budget Tier (Budget/Moderate/Luxury), Travel Styles (multi-select), Output Language.
  - Actions: Generate Plan, Q&A (contextual), Export PDF.
  - Holds transient data in session state.

- **Prompt Orchestrator (Client-Side Module)**
  - Builds a structured prompt from user inputs and output constraints (Markdown, ~600 words, sections, sources).

- **AI Generation (External Service)**
  - Groq Llama API returns the initial travel plan.

- **Search/Enrichment (External Service)**
  - SerpAPI fetches reliable links and up-to-date references (hotels/attractions/infos).

- **Plan Post-Processor (Client-Side Module)**
  - Merges AI text with enriched links; ensures sections exist; normalizes the final Markdown.

- **PDF Exporter (Client-Side Module)**
  - Converts rendered Markdown into a downloadable PDF.

> **Note:** There is **no server back-end** in the MVP.  
> If needed later, a thin API layer can be introduced without breaking the current UI.

---

## 2. Define Components, Classes, and Database Design

### Purpose
To detail the internal structure of the system components for the MVP. Since this project is front-end focused with no persistence requirements, the documentation explains the in-memory model and outlines how components interact without back-end or database dependencies.

### 1) Back-End Components
- No back-end service is included in the MVP.
- All logic is handled client-side within the Streamlit application.
- If persistence or APIs are required in the future, a thin back-end layer (e.g., FastAPI/Node.js) can be added with minimal refactoring.

### 2) Data Model (In-Memory – No DB)
The app keeps transient state only; no persistence beyond the session.

Example JSON structure:
{
  "inputs": {
    "destination": "string",
    "duration": 1,
    "budgetTier": "Budget | Moderate | Luxury",
    "travelStyles": ["Culture", "Nature", "Adventure", "Relaxation", "Food", "Shopping"],
    "language": "Arabic | English"
  },
  "plan": "Markdown string (final enriched plan)",
  "qa": [
    { "q": "string", "a": "Markdown string" }
  ]
}

### 3) Database (Future Consideration)
No Database (ERD/Collections) for MVP

No database is required for the MVP. If persistence is introduced later:

Relational Example (SQL):
plans(id, destination, duration, budget, styles_json, language, plan_md, created_at)

Document Example (JSON):
plans {
  "destination": "Paris",
  "duration": "7 days",
  "budget": "medium",
  "styles": ["cultural", "culinary"],
  "language": "English",
  "plan_md": "...",
  "created_at": "2025-09-22"
}

### 4) Front-End UI Components & Interactions
- Inputs Panel (Centered Form): destination, duration, budgetTier, travelStyles, language, [Generate]
- Plan View: summary (chips) + sections (best time, itinerary, accommodations, culinary, tips, cost)
- Q&A Expander: question → answer grounded in current plan
- Export: [Download PDF]

Interaction Flow (High-Level):
1. User fills inputs → PromptOrchestrator builds structured prompt
2. AiClient (LLM API) generates draft plan
3. SearchClient (SerpAPI) fetches supporting links/details
4. PlanComposer merges and normalizes → UI renders Markdown
5. (Optional) QA uses current plan as context
6. Export via PdfService

### 5) Technical Justification
- No Back-End / No DB: not a current requirement; reduces complexity and time-to-value
- LLM + SerpAPI: cover computation and fresh references without storing user data
- In-Memory State: sufficient for single-session usage; avoids authentication/storage overhead
- Future-Ready: a server API or persistence layer can be added later with minimal refactoring

