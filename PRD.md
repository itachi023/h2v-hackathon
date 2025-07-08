# Sahayak – AI Teaching Assistant

## Product Requirements Document (PRD)

## 1. Purpose & Vision

Sahayak is an AI-powered companion designed for teachers who juggle multiple grades in low-resource classrooms. The product’s north-star is to **reduce preparation time and amplify instructional impact** by automatically generating localized, differentiated learning materials and simple assessments.

---

## 2. Problem Statement (Why now?)

1. One teacher often handles several grade levels simultaneously.
2. Limited time and tools to create culturally relevant content.
3. Difficulty personalising lessons and tracking diverse learning needs.
4. Lack of quick-turnaround assessments and visual aids.

---

## 3. Goals

• **Goals**

  1. Empower teachers to create/curate learning assets in minutes, not hours.
  2. Support multiple Indian languages out-of-the-box.
  3. Offer a single, low-friction dashboard that works on desktop and mobile browsers.

<!-- • **Non-Goals (MVP)**
  – Deep analytics at district/school level.
  – Advanced cost optimisation or large-scale performance tuning.
  – Full offline functionality. -->

---

## 4. Success Indicators (Demo-day metrics)

* < 5 clicks to produce and share a worksheet & slide deck.
* Teacher creation flow completes in < 2 min on a live demo.
* Positive qualitative feedback from 3 target teachers in user testing.

---

## 5. User Personas

1. **Primary – Multi-grade Teacher (Priya, 32)**
   • Teaches Grades 3-5 in a rural government school.
   • Has basic smartphone and occasional computer lab access.
   • Limited prep time (~2 hrs/week outside class).

2. **Secondary – Head Teacher/Cluster Coordinator**
   • Oversees academic quality & may want summary analytics.

---

## 6. Core User Journey (Hero Flow)

1. Priya logs in with Google.
2. Selects Marathi as preferred language.
3. Uploads either a photo of a textbook page **or an entire book (PDF/scan)** for automatic processing.
4. Chooses Grade 3-5 differentiation.
5. Clicks “Generate”.
6. System returns:
   • Worksheet PDFs (grade-wise)
   • Google Slides deck covering the concept
   • Short answer key saved to knowledge base
7. Priya shares links/prints materials for class.

---

## 7. Scope

### 7.1 MUST-HAVE (We Will Build in 10 Days)

1. **Multi-language Dashboard:** language picker stored in user settings.
2. **Knowledge Base Uploads:** PDF/image ingestion → embeddings stored (Mem0 + vector DB).
3. **Chat-based Agent:** quick Q&A using the knowledge base + Gemini.
4. **Content Generation:**
   • Hyper-local text/story creation.
   • Differentiated worksheet generator (single concept).
5. **Visual Aid Creation:** auto-generated Google Slides deck via Slides API.
6. **Assessment Lite:** generate 5-question MCQ quiz + answer key.
7. **Basic Sharing:** download PDFs and auto-share Google Slides link.

### 7.2 STRETCH GOALS (If Time Allows)

A. **Formative Quiz Engine:** live quiz conduction & auto-grading with chart.
B. **Speech-to-Text Reading Assessment** leveraging Vertex AI STT.
C. **Weekly Lesson Planner** auto-drafted from syllabus & KB.
D. **Teacher Feedback Loop:** ability to correct AI answers → retrain embeddings in Mem0.
E. **WhatsApp / SMS Distribution** links for low-bandwidth sharing.

---

## 8. Feature Requirements (MVP)

| # | Feature | Description | Acceptance Criteria |
|---|---------|-------------|----------------------|
| 1 | Language Setting | User selects preferred language once; UI text & AI output localised. | a) Setting persists across sessions. b) All generated content in chosen language. |
| 2 | KB Upload | Accept PDF/JPEG/PNG; store embeddings. | Upload < 10 MB completes; file appears in “My Resources”. |
| 3 | Agent Chat | Chat window answers in ≤ 5s for typical queries. | Correct answer > 80% in internal test set. |
| 4 | Worksheet Gen | Generates grade-wise PDFs (≤ 2 pages each). | Downloads open & contain at least 3 unique questions. |
| 5 | Slides Deck | 5–7 slide deck with text + simple images. | Deck appears in teacher’s Drive and share link displayed. |
| 6 | Quiz Lite | MCQ quiz JSON & printable PDF answer sheet. | Teacher can preview and download. |

---

## 9. High-Level Architecture (Light)

• **Frontend:** React + Firebase Hosting.
• **Backend:** FastAPI server on Cloud Run, housing Gemini calls & Slide/Docs API orchestration.
• **Auth:** Google Identity (OAuth) → Firebase Auth.
• **Vector Store:** Open-source vector DB (e.g., Qdrant) + Mem0 for memory.

---

## 10. Timeline (10 Days)

| Day | Milestone |
|-----|-----------|
| 1-2 | Setup repo, auth, language selector, KB upload stub |
| 3-4 | Gemini integration for content gen & chat |
| 5-6 | Slides API + PDF generation |
| 7   | Worksheet differentiation logic |
| 8   | Quiz Lite & basic analytics |
| 9   | Polish UI, localisation strings |
| 10  | Buffer, user testing, demo video |

---

## 11. Open Questions

1. What syllabus mapping (NCERT vs state boards) is required day-one?
2. Minimum device/browser support matrix.
3. Long-term storage vs. auto-purge policy for uploads.

---

## 12. Out-of-Scope (MVP)

* Cost optimisation, scaling to >1K teachers.
* Detailed student progress dashboards.
* Integration with school MIS.

---

## 13. Appendix – References

• Google Slides API Overview  
• Google Docs API Create Document  
• Mem0 open-source memory framework
