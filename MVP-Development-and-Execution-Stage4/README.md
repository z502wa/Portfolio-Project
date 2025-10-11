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


# Task 1: Execute Development Tasks  
**Mandatory**

## Purpose  
To implement features and deliverables according to the sprint plan, ensuring development aligns with coding standards, SCM practices, and QA testing.

---

## Execution Process

### Developers  
- Implement assigned features from the sprint backlog.  
- Follow agreed coding standards and documentation guidelines.  
- Commit code frequently to feature branches with clear commit messages.  

### Source Control Manager (SCM)  
- Enforce Git branching strategy (feature branches → pull requests → development branch → main).  
- Review pull requests to ensure code quality and consistency.  
- Resolve conflicts and maintain branch integrity.  

### Quality Assurance (QA)  
- Test completed features immediately after development.  
- Conduct **unit tests** (functionality of each component) and **integration tests** (end-to-end flow).  
- Report bugs or performance issues back to developers.  

---

## Example: API Feature Development  
- **Developer**: Implements an API endpoint to fetch travel plan data.  
- **SCM**: Reviews and merges the pull request after validation.  
- **QA**: Uses Postman to test endpoint responses for accuracy and reliability.  

---

## Deliverables  
- Completed and reviewed features merged into the development branch.  
- QA test reports on completed features.  
- Updated documentation (if required).  

---

## Task 2. Monitor Progress and Adjust  
**Mandatory**

### Purpose
To track team performance, measure progress, and address any issues during the sprint.

---

### Approach

#### 1. Daily Stand-Ups
- Short daily meetings (10–15 minutes).
- Each team member answers:
  - What did I complete yesterday?
  - What will I work on today?
  - Do I have any blockers?

#### 2. Project Management Tools
- Use **Trello** (or Jira) to manage tasks.
- Tasks are represented as cards moving across boards:
  - **To Do → In Progress → Done**
- Provides transparency and progress tracking for all stakeholders.

#### 3. Metrics for Progress Tracking
- **Sprint Velocity**: Number of tasks completed in each sprint.
- **Completion Rate**: % of tasks completed vs. planned.
- **Bug Count & Resolution Rate**: Track number of issues and time to resolve them.

#### 4. Adjustments
- If delays or blockers occur:
  - Reassign tasks across team members.
  - Adjust sprint goals based on capacity and priorities.
- Objective: Keep the MVP development on track and within timeline.

---

### Example
For a two-week sprint:
- **Daily Stand-Up**: Quick updates and blockers shared.
- **End of Week Review**: Track progress (e.g., 5 out of 7 tasks completed → 71% completion).
- **Adjustment**: Shift pending tasks to next sprint or redistribute workload.

---

### Deliverable
A monitoring strategy including:
- Daily Stand-Up plan.
- Trello board setup for task tracking.
- Metrics definition (velocity, completion %, bug resolution).
- Adjustment process for blockers and delays.


