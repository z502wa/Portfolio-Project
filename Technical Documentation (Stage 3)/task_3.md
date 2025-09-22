
# Task 3: Create High-Level Sequence Diagrams

## Purpose
To show how components or services interact for key use cases in the Smart Travel Website MVP.

---

## Key Use Cases
1. **Generate Travel Plan**
   - Traveler enters inputs (destination, duration, budget, travel styles, language).
   - System builds a structured prompt.
   - LLM generates a draft plan.
   - SerpAPI enriches the plan with current hotels/attractions.
   - PlanComposer merges content and normalizes structure.
   - UI renders final Markdown plan.

2. **Ask a Question (Q&A)**  
   - Traveler submits a follow-up question.  
   - System uses current travel plan as context.  
   - LLM generates a concise, contextualized answer.  
   - UI displays the answer under the Q&A expander.

3. **Export Plan as PDF**  
   - Traveler clicks "Download PDF".  
   - PdfService formats Markdown content.  
   - System generates a styled PDF file.  
   - Traveler downloads the plan.

---

## Sequence Diagrams

### 1) Generate Travel Plan
```mermaid
sequenceDiagram
    participant U as User
    participant FE as Streamlit UI
    participant PB as Prompt Builder
    participant LLM as Groq Llama API
    participant SA as SerpAPI
    participant PC as Plan Composer

    U->>FE: Enter inputs (destination, days, budget, styles, language)
    FE->>PB: Send inputs
    PB->>LLM: Build + send structured prompt
    LLM-->>PB: Draft plan (Markdown)
    PB->>SA: Request hotels/attractions
    SA-->>PB: JSON links/details
    PB->>PC: Merge draft + links
    PC-->>FE: Final enriched plan (Markdown)
    FE-->>U: Display travel plan
```

### 2) Q&A on Plan
```mermaid
sequenceDiagram
    participant U as User
    participant FE as Streamlit UI
    participant QA as Q&A Orchestrator
    participant LLM as Groq Llama API

    U->>FE: Ask question
    FE->>QA: Send question + current plan
    QA->>LLM: Build contextual prompt
    LLM-->>QA: Answer (Markdown)
    QA-->>FE: Return answer
    FE-->>U: Display answer under Q&A section
```

### 3) Export Plan as PDF
```mermaid
sequenceDiagram
    participant U as User
    participant FE as Streamlit UI
    participant PDF as PdfService

    U->>FE: Click "Download PDF"
    FE->>PDF: Send Markdown content
    PDF-->>FE: Return formatted PDF
    FE-->>U: Trigger download
```

---

## Deliverables
- Three sequence diagrams showing interactions for:
  1. Travel plan generation.  
  2. Question answering.  
  3. Exporting plan as PDF.
