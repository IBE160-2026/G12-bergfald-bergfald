**PRODUCT BRIEF · BMAD METHOD V6.11.0 TEMPLATE**

# Jippy

*Your friend Jippy: the AI study buddy that turns your own notes into summaries, flashcards and quizzes.*

**Status** Draft v1.0 · **Date** 25 September 2026 · **Primary user** University students · **Model** Freemium

---

## 1. Executive Summary

University students often have plenty of study material and too little time to turn it into practice. **Jippy** is an AI study buddy we are building for them. It turns the material they already have (lecture slides, PDFs, readings and their own notes) into summaries, flashcards and practice quizzes in minutes. Today a lot of study time goes into *preparing* to study: rewriting notes, typing flashcards and searching for practice questions that match the course. When time runs short, students fall back on rereading and highlighting, which feel productive but work less well than testing yourself.

Jippy removes that setup work. A student uploads a lecture or pastes notes, and Jippy builds a study set from **that exact material**: a short summary, an editable flashcard deck and a quiz. Each answer links back to the part of the source it came from. The student reviews, corrects and practises in one place, and Jippy shows which topics still need work.

**Why now:** AI can now read long documents and write good questions from them cheaply, and many students already paste their notes into general chatbots to study. Those chatbots don't keep the material organised, don't save anything as a reusable study set, and can make things up. Jippy puts the same capability into a focused study workflow that students can trust.

## 2. The Problem

**Who hurts:** university students with a heavy reading or memorisation load (e.g. medicine, law, biology, economics), especially in the weeks before exams.

**What they do today:**

- Reread slides and highlight: easy, but they remember little of it.
- Make flashcards by hand in Anki or Quizlet: this works, but it is slow.
- Paste notes into a general chatbot: fast, but nothing is saved or structured, and it can invent facts.
- Use decks other students made, which rarely match their own lecturer's content.

**Cost of the status quo:** hours each week spent on preparation instead of practice, an ongoing trade-off between speed and studying well, and pre-exam stress because they can't tell what they actually know.

## 3. The Solution

Jippy is a study companion organised by subject. The student adds course material, and Jippy turns it into:

- **Summaries** that condense a lecture into its key ideas;
- **Flashcards** the student can edit, keep or discard;
- **Quizzes** with instant feedback, where each wrong answer points back to the right passage in the source.

**What changes for the user:** an evening spent making flashcards becomes 10 minutes spent checking cards Jippy made. Instead of wondering "Am I ready?", students can see which topics they are weak on and what to review next.

> **Deliberately not specified yet:** which AI model to use, the review/spaced-repetition algorithm, web vs. mobile implementation details and exact prices. These belong in the PRD and architecture.

## 4. What Makes This Different

| Alternative today | Why users tolerate it | Why Jippy is better |
|---|---|---|
| **General AI chatbots** | Already open, free and flexible | Answers come only from the student's own files, with links to the source. Results are saved as study sets, and the output is built for practice rather than being a block of text. |
| **Manual flashcard apps (Anki, Quizlet)** | Proven, familiar, good review systems | Jippy writes the cards from the student's own material, so the student edits cards instead of typing them. It also adds summaries and quizzes. |
| **Rereading and highlighting** | No setup, feels productive | Jippy makes testing yourself almost as effortless as rereading. |
| **Shared or pre-made decks** | Free and instantly available | Jippy's material is built from *this* course and *this* lecturer's content. |

> **Honest advantage:** the underlying AI is available to anyone, and existing tools (e.g. Quizlet) are adding AI features. Jippy's edge is a **tighter workflow** (upload → study set → practice → review weak spots) and **trust through links to the source**, not proprietary technology. We have to win on execution and student experience.

## 5. Who This Serves

> **Primary user:** a university student with a heavy course load who has plenty of material but too little time, and wants to turn it into real practice before exams.

**What they need:** speed (a study set within minutes), trust (content that is accurate and checkable), a match with their own course, and tolerance for messy real-world notes.

**What success looks like in their day:** "*I uploaded today's lecture after class, did a 10-minute quiz on the bus, and now I know exactly which two topics to review tonight.*"

**Secondary users (later):** high-school students, self-learners studying for certifications, and tutors or lecturers who want to give their students study sets.

## 6. Success Criteria

| Signal | Metric / evidence | Target | When measured |
|---|---|---|---|
| **User outcome** | Time from upload to first study session; share of students who say they feel better prepared | < 5 min; ≥ 70% say "better prepared" | In-app timing; survey after the first exam period |
| **Adoption / behaviour** | Users who complete a quiz or flashcard session each week; share still active in week 4 | ≥ 40% weekly active; ≥ 30% four-week retention | Weekly, from the first week of the pilot |
| **Quality / trust** | Share of generated cards and questions kept without major edits; items flagged as wrong | ≥ 80% kept; < 2% flagged | Continuously, via an in-app "flag" button |
| **Business / mission** | Free-to-paid conversion; AI cost per active user compared with plan price | 3–5% convert; healthy margin on paid plan | Monthly, after the paid plan launches |

*All targets are starting assumptions and will be checked and adjusted during a pilot with one or two student cohorts.*

## 7. Scope

### IN: first version

1. Upload PDFs/slides and paste or type notes, organised by subject
2. Generate summaries from the uploaded material
3. Generate editable flashcards with a simple review mode
4. Generate practice quizzes with feedback and links to the source
5. Accounts with freemium limits (monthly free cap, paid upgrade)

### OUT: not now

1. Photos of handwritten notes, audio/video lecture transcription
2. Sharing decks, study groups and collaboration
3. Native mobile apps (start with a mobile-friendly web app)
4. Integrations with university learning platforms (Canvas, Moodle etc.)
5. Open-ended AI tutor chat and homework solving

**Scope test:** every IN item is needed to show the core value, which is going from your material to active practice in minutes. The OUT items could all be removed and we could still test that.

## 8. Vision

| NOW — First version | NEXT — Expanded use | 2–3 YEARS — Vision |
|---|---|---|
| Upload → summary, flashcards, quiz. Show that students practise more with less preparation. | Spaced repetition and weak-topic tracking, a mobile app, photo and lecture-recording input, and sharing decks with classmates. | A study companion for the whole degree that plans your exam prep and explains concepts from your own course material. |

> **Vision statement:** Every student has a study buddy that knows their courses as well as they do. Jippy remembers everything they have studied, plans revision before each exam, explains difficult concepts using their own lecture material, and works with lecturers on course-approved study sets. Students spend their time learning instead of preparing to learn.

## + Key Assumptions to Validate

- **Biggest assumption:** AI-generated flashcards and questions are accurate and relevant enough that students trust them and don't rewrite them all.
- Students will use Jippy regularly during the semester, not only in the week before an exam.
- Enough heavy users will pay for a premium plan to cover AI costs for the free tier.

---

*Jippy · Product Brief · Draft v1.0 · 25 September 2026 · Based on the BMAD Method v6.11.0 student product brief template*
