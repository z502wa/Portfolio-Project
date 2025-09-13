# Project Charter – Smart Travel Website  

## Project Objectives
- **Purpose:** Simplify travel planning by generating personalized itineraries based on user preferences, budget, and travel styles.  
- **Objectives:**  
  1. Provide destination suggestions aligned with the user’s budget and travel duration.  
  2. Deliver detailed cost breakdowns, accommodations, and attractions.  
  3. Include essential safety and practical travel tips.  

---

## Stakeholders and Roles
- **Internal:** Team members, tutors/instructors.  
- **External:** End-users (travelers), industry experts (optional).  

| Team Member        | Role                   | Responsibilities                                                |
|--------------------|------------------------|----------------------------------------------------------------|
| Hamad Dahash       | Project Manager        | Oversees planning, ensures deadlines, manages communication.   |
| Suhail Alaboud     | Implementation Lead    | Leads execution, implements core features, ensures technical quality. |
| Khaled Aldawsari   | Research & Documentation | Supports research, documents progress, assists with design.    |
| Abrar Almukhlaifi  | Support & Testing      | Assists in testing, provides feedback, supports non-technical tasks. |

---

## Scope
**In-Scope (MVP):**  
- Destination-based plan generation.  
- Structured itinerary with cost breakdown.  
- Accommodation recommendations.  
- Safety and practical tips.  
- Bilingual output (Arabic/English).  
- Web interface (Streamlit).  

**Out-of-Scope:**  
- Direct bookings.  
- Real-time price guarantees.  
- User accounts and profiles.  
- Mobile apps (web-only MVP).  
- Visa, insurance, or legal services.  

---

## Risks
| Risk                     | Mitigation Strategy                                    |
|--------------------------|--------------------------------------------------------|
| API Integration Challenges | Test APIs early, use fallback datasets.              |
| Data Accuracy & Updates  | Use trusted sources, schedule validations.             |
| Timeline Delays          | Break tasks into smaller deliverables.                 |
| Team Availability        | Assign critical tasks to Implementation Lead.          |
| Security Concerns        | Include safety tips, verified links.                   |

---

## High-Level Plan
| Stage | Timeline | Deliverables |
|-------|----------|--------------|
| Stage 1: Idea Development | Week 1–2 | Stage 1 Report |
| Stage 2: Project Charter Development | Week 3–4 | Project Charter |
| Stage 3: Technical Documentation | Week 5–6 | Tech Docs |
| Stage 4: MVP Development | Week 7–10 | Working MVP |
| Stage 5: Project Closure | Week 11–12 | Final Report & Handover |

```mermaid
gantt
    title Project Timeline - Smart Travel Website
    dateFormat  YYYY-MM-DD
    excludes    weekends

    section Stage 1
    Idea Development :done, s1, 2025-08-25, 2025-09-07

    section Stage 2
    Project Charter Development :active, s2, 2025-09-08, 2025-09-21

    section Stage 3
    Technical Documentation : s3, 2025-09-22, 2025-10-05

    section Stage 4
    MVP Development (Build) : s4a, 2025-10-06, 2025-11-02
    MVP Integration & Polish : s4b, 2025-11-03, 2025-11-09

    section Stage 5
    Testing & Final Presentation : s5a, 2025-11-10, 2025-11-23
    Closure & Handover : s5b, 2025-11-24, 2025-11-30
