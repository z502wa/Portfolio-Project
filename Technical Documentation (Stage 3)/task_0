# Stage 3 — Technical Documentation  
## Task 0: Define User Stories and Mockups  

---

### 1. Inputs & Preferences (from current code)
- **Destination** *(text)*: User manually enters the city/target destination.  
- **Duration** *(number)*: Trip length (1–30 days).  
- **Budget** *(select slider)*: Options are **Budget | Moderate | Luxury**.  
- **Travel Styles** *(multi-select)*: `Culture`, `Nature`, `Adventure`, `Relaxation`, `Food`, `Shopping`.  
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

#### Won't Have
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
   - Input: "Ask a question about your plan..."  
   - Answer: Shown in Markdown, grounded in the generated plan.  
   - Empty State: "Generate a plan first."  

---

### 4. UI Mockup Preview  

![Smart Traveler UI](https://github.com/z502wa/Portfolio-Project/blob/main/Technical%20Documentation%20(Stage%203)/ui_mockup.png)

---

### 5. Notes for Implementation
- **Prompting:** Structured input sent to AI (Groq Llama) including user data and instructions.  
- **Source Links:** Verified using SerpAPI to fetch live, accurate references.
