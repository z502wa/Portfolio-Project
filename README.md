# Project Charter – Smart Travel Website (Detailed Version) (Stage 2)

---

## Task 0: Project Objectives
- **Purpose:** Simplify travel planning by generating personalized itineraries based on user preferences, budget, and travel styles.  

- **Objectives:**  
  1. Provide destination suggestions aligned with the user’s budget and travel duration.  
  2. Deliver detailed cost breakdowns, accommodations, and attractions.  
  3. Include essential safety and practical travel tips.  

---

## Task 1: Identify Stakeholders and Team Roles

### Stakeholders
- **Internal:** Team members, tutors/instructors.  
- **External:** End-users (travelers), industry experts (optional).  

### Roles
| Team Member | Role | Responsibilities |
|-------------|------|------------------|
| Hamad Dahash | Project Manager | Oversees planning, ensures deadlines, manages communication. |
| Suhail Alaboud | Implementation Lead | Leads execution, implements core features, ensures technical quality. |
| Khaled Aldawsari | Research & Documentation | Supports research, documents progress, assists with design. |
| Abrar Almukhlaifi | Support & Testing | Assists in testing, provides feedback, supports non-technical tasks. |

---

## Task 2: Define Scope

### High-Level Scope Statement
The Smart Travel Website will generate a personalized, source-backed travel plan based on a user’s destination, trip duration, budget tier, and travel styles. It produces a concise itinerary with accommodation suggestions, safety and practical tips, and an estimated total cost—plus a compact Q&A experience grounded in the generated plan.

### In-Scope (MVP)
- Destination-based plan generation (budget, styles, duration).  
- Structured day-by-day itinerary.  
- Accommodation suggestions.  
- Estimated total cost with money-saving tips.  
- Safety & practical tips.  
- Attractions & culinary highlights.  
- Bilingual output (Arabic/English).  
- Q&A module based on the generated plan.  
- Web interface (Streamlit).  

### Out-of-Scope (for MVP)
- Direct bookings (flights, hotels, activities).  
- Real-time price guarantees.  
- User accounts or saved profiles.  
- Advanced AI chatbot beyond plan-grounded Q&A.  
- Mobile applications (iOS/Android).  
- Visa processing, insurance brokerage, or legal advisory.  
- Offline mode or downloadable maps.  
- Complex personalization (no long-term learning).  
- Back-office dashboards/analytics.  

---

## Task 3: Identify Risks

| Risk | Description | Mitigation Strategy |
|------|-------------|---------------------|
| API Integration Challenges | Difficulty connecting travel APIs. | Test APIs early, use fallback datasets. |
| Data Accuracy & Updates | Outdated info could reduce reliability. | Use trusted sources, schedule validations. |
| Timeline Delays | Technical blockers or learning curve. | Break tasks into smaller deliverables. |
| Team Availability | Some members may not contribute consistently. | Assign critical tasks to Implementation Lead. |
| Scalability Limitations | MVP may not handle heavy load. | Focus on MVP first; modular design for future. |
| User Adoption Risk | Low engagement from users. | Collect feedback, adjust features. |
| Security Concerns | Lack of safety context in recommendations. | Include safety tips, verified official links. |

---

## Task 4: Develop a High-Level Plan

### Phases & Milestones
| Stage | Timeline (Weeks) | Description | Deliverables |
|-------|------------------|-------------|--------------|
| Stage 1: Idea Development | Week 1–2 | Team formation, brainstorming, MVP selection | Stage 1 Report |
| Stage 2: Project Charter Development | Week 3–4 | Objectives, stakeholders, scope, risks, plan | Project Charter |
| Stage 3: Technical Documentation | Week 5–6 | Architecture, data flow, requirements | Technical Docs |
| Stage 4: MVP Development | Week 7–10 | Build Smart Travel MVP | Working MVP |
| Stage 5: Project Closure | Week 11–12 | Testing, final presentation, retrospective | Final Report & Handover |

### High-Level Timeline (Gantt)
```mermaid
gantt
    title Project Timeline - Smart Travel Website
    dateFormat  YYYY-MM-DD
    excludes    weekends

    section Stage 1
    Idea Development            :done,    s1, 2025-08-25, 2025-09-07

    section Stage 2
    Project Charter Development :active,  s2, 2025-09-08, 2025-09-21

    section Stage 3
    Technical Documentation     :        s3, 2025-09-22, 2025-10-05

    section Stage 4
    MVP Development (Build)     :        s4a, 2025-10-06, 2025-11-02
    MVP Integration & Polish    :        s4b, 2025-11-03, 2025-11-09

    section Stage 5
    Testing & Final Presentation:        s5a, 2025-11-10, 2025-11-23
    Closure & Handover          :        s5b, 2025-11-24, 2025-11-30
