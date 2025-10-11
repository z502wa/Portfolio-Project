# Stage 4 – Task 0: Sprint Planning

## Purpose
To divide the development phase into short, manageable iterations, prioritize tasks, and assign responsibilities to ensure efficient delivery of the MVP.

---

## Sprint Overview

- **Sprint Duration**: 2 weeks each  
- **Number of Sprints**: 2 (initial MVP focus + enhancements)  
- **Framework**: MoSCoW prioritization (Must Have, Should Have, Could Have, Won’t Have)  

---

## Sprint 1 – Core MVP (Must Have)

**Duration**: 2 weeks  
**Goals**: Implement the essential MVP flow: input form → AI prompt → plan generation → display results.  

**Tasks**:
- Build centered input form (destination, duration, budget, styles, language, [Generate]).
- Implement `PromptOrchestrator` to structure prompt from user inputs.
- Connect to AI client (LLM) to generate draft plan.
- Connect to SerpAPI to fetch references and details.
- Merge results into unified Markdown plan (PlanComposer).
- Display plan in UI with sections (itinerary, cost, accommodations, tips).

**Dependencies**:
- Input form must be completed before PromptOrchestrator.  
- PromptOrchestrator and AI client integration must be done before PlanComposer.  

**Team Responsibilities**:
- Frontend Dev: Input form + results display.  
- Backend/API Dev: AI + SerpAPI integration, orchestration.  
- QA: Test input–output flow.  
- SCM: Review pull requests, enforce branch strategy.  

---

## Sprint 2 – Enhancements (Should Have)

**Duration**: 2 weeks  
**Goals**: Add additional features and polish.  

**Tasks**:
- Add Q&A Expander: user questions → answers from current plan.  
- Add export to PDF.  
- Improve UI/UX (styling, background image, responsive design).  
- Add error handling for API failures.  

**Dependencies**:
- Core MVP (Sprint 1) must be fully functional.  
- PDF export depends on finalized plan structure.  

**Team Responsibilities**:
- Frontend Dev: Q&A section, PDF export button, UI polish.  
- Backend/API Dev: Q&A context retrieval.  
- QA: Test Q&A, PDF export.  
- SCM: Review and merge changes.  

---

## Prioritization (MoSCoW)

- **Must Have**: Input form, AI integration, SerpAPI, plan display.  
- **Should Have**: Q&A, PDF export, UI polish.  
- **Could Have**: Email export (future sprints).  
- **Won’t Have (for MVP)**: Booking integration (flights, hotels).  

---

## Timeline (Gantt-style overview)

- **Week 1–2**: Sprint 1 (Core MVP).  
- **Week 3–4**: Sprint 2 (Enhancements).  
- **Week 5**: Final QA, bug fixes, integration testing.  

---

## Deliverable

A sprint plan with prioritized tasks, clear responsibilities, and deadlines for all team members to guide MVP development.
