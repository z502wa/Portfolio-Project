# Stage 3 — Technical Documentation  
## Task 0: Define User Stories and Mockups  

---

### 1. Inputs & Preferences (from current code)
- **Destination** *(text)*: User manually enters the city/target destination.  
- **Duration** *(number)*: Trip length (1–30 days).  
- **Budget** *(select slider)*: Options are **Budget | Moderate | Luxury**.  
- **Travel Styles** *(multi-select)*: `Culture, Nature, Adventure, Relaxation, Food, Shopping`.  
- **Answer Language** *(select)*: **Arabic | English** (output language only).  
- **Primary Actions**:  
  - **Generate My Perfect Travel Plan** → Structured prompt sent to the AI model, returning:  
    1. Best Time to Visit  
    2. Accommodation Recommendations (budget-aware)  
    3. Day-by-Day Itinerary  
    4. Culinary Experiences  
    5. Practical & Safety Tips (transport, etiquette, safety, daily budget)  
    6. Estimated Total Trip Cost + money-saving tips  
    + Source links included.  
  - **Q&A (Expander)** → Ask follow-up questions based on the generated plan.  

---

### 2. User Stories (MoSCoW Prioritization)

#### Must Have
1. **Enter destination and trip details**  
   *As a traveler, I want to enter my destination, duration, budget, and travel style, so that I can get a tailored plan.*  

2. **Generate an AI-based travel plan**  
   *As a traveler, I want to generate a structured travel plan, so that I can quickly organize my trip.*  

3. **Source-backed recommendations**  
   *As a traveler, I want the plan to include reliable source links, so that I can verify recommendations.*  

4. **Language toggle for output**  
   *As a traveler, I want to choose Arabic or English for my plan, so that I can read it comfortably.*  

#### Should Have
5. **Budget-aware accommodations**  
   *As a traveler, I want hotel suggestions aligned with my budget, so that I can book confidently.*  

6. **Q&A grounded in the generated plan**  
   *As a traveler, I want to ask clarifying questions, so that I can refine details without starting over.*  

7. **Export plan as PDF**  
   *As a traveler, I want to export my plan as a PDF, so that I can save or share it.*  

#### Could Have
8. **Email plan to myself**  
   *As a traveler, I want to send my plan to my email, so that I can access it later.*  

#### Won’t Have
9. **Automatic destination suggestions** → Out of scope.  
10. **In-app bookings** → Out of scope.  

---

### 3. Mockups (Wireframe Descriptions)

1. **Screen A — Trip Settings (Centered Form)**  
   - Fields: Destination, Duration, Budget, Travel Styles, Answer Language, [Generate Plan].  
   - Layout: Clean vertical layout in the **center of the page**.  
   - Background: A collage of travel destinations with a subtle overlay.  

2. **Screen B — Plan View**  
   - Header: Destination, Duration, Budget, Styles (summary).  
   - Sections: Best Time to Visit, Day-by-Day Itinerary, Accommodations, Culinary Experiences, Practical & Safety Tips, Estimated Cost.  
   - Footer: [Export PDF] [Regenerate Plan].  

3. **Screen C — Q&A Panel**  
   - Input: “Ask a question about your plan…”  
   - Answer: Shown in Markdown, grounded in the generated plan.  
   - Empty State: “Generate a plan first.”  

---

### 4. UI Mockup Preview  

![Smart Traveler UI](https://github.com/z502wa/Portfolio-Project/blob/main/Technical%20Documentation%20(Stage%203)/ui_mockup.png)

---

### 5. Notes for Implementation
- **Prompting:** Structured input sent to AI (Groq Llama) including user data and instructions.  
- **Source Links:** Verified using SerpAPI to fetch live, accurate references.  


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

---

### 1) Back-End Components
- **No back-end service** is included in the MVP.  
- All logic is handled client-side within the Streamlit application.  
- If persistence or APIs are required in the future, a thin back-end layer (e.g., FastAPI / Node.js) can be added with minimal refactoring.  

---

### 2) Data Model (In-Memory – No DB)
The app keeps transient state only; no persistence beyond the session.

```json
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
3) Database (Future Consideration)
No Database (ERD/Collections) for MVP
No database is required for the MVP.
If persistence is introduced later:

Relational Example:

sql
Copy code
plans(id, destination, duration, budget, styles_json, language, plan_md, created_at)
Document Example:

json
Copy code
plans {
  "destination": "Paris",
  "duration": "7 days",
  "budget": "medium",
  "styles": ["cultural", "culinary"],
  "language": "English",
  "plan_md": "...",
  "created_at": "2025-09-22"
}
4) Front-End UI Components & Interactions
Inputs Panel (Centered Form): destination, duration, budgetTier, travelStyles, language, [Generate].

Plan View: summary (chips) + sections (best time, itinerary, accommodations, culinary, tips, cost).

Q&A Expander: question → answer grounded in current plan.

Export: [Download PDF].

Interaction Flow (High-Level):

User fills inputs → PromptOrchestrator builds structured prompt.

AiClient (LLM API) generates draft plan.

SearchClient (SerpAPI) fetches supporting links/details.

PlanComposer merges and normalizes → UI renders Markdown.

(Optional) QA uses current plan as context.

Export via PdfService.

5) Technical Justification
No Back-End / No DB: not a current requirement; reduces complexity and time-to-value.

LLM + SerpAPI: cover computation and fresh references without storing user data.

In-Memory State: sufficient for single-session usage; avoids authentication/storage overhead.

Future-Ready: a server API or persistence layer can be added later with minimal refactoring.

yaml
Copy code
