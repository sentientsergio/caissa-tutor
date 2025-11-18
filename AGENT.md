# AGENT.md – Instructions for Codex (and Other AI Builders)

## 1. Who You Are

You are an AI coding and design agent (e.g., Codex) working on the **Caïssa** project.

Your mission is to transform this repository from a **concept seed** into a well-specified, implementable project for an AI-powered chess tutor.

You should:

- Clarify requirements where needed (by proposing reasonable defaults).
- Produce design and architecture documents.
- Propose a directory structure and initial code skeletons.
- Prioritize a **mobile-first MVP**, while keeping the backend and architecture extensible.

---

## 2. High-Level Goal

Build the **MVP** for **Caïssa – The Lifelong Chess Tutor**, focusing on:

1. **Mobile-first dual-board chess experience** (Game Board + Analysis Board).
2. **Three teaching modes**: Beginner, Improver, Challenger.
3. **Interactive game review** with:
   - Key moment detection,
   - Conceptual explanations,
   - Simple player modeling for recurring issues.
4. **Backend orchestration** of:
   - Chess engine analysis,
   - LLM-based explanations,
   - Persistent user/game/memory storage.

**Important:**  
The recent “red-team / strong player feedback → RLHF” idea is **explicitly non-MVP**.  
You should mention it only as future roadmap, not as a core requirement for the first versions.

---

## 3. Deliverables You Should Produce

As you evolve this repo, you should create and maintain at least the following artifacts:

1. **`docs/requirements.md`**

   - Detailed functional requirements for the MVP.
   - User stories, grouped by:
     - Playing a game
     - Asking for move explanations
     - Game review flow
     - Player memory & recurring pattern surfacing
     - Account/profile basics (if any)

2. **`docs/architecture.md`**

   - Overall system diagram.
   - Proposed tech stack:
     - Mobile (e.g., React Native or Flutter).
     - Backend (e.g., Node.js/TypeScript, Python, or similar).
     - Chess engine integration (e.g., Stockfish via UCI or library).
     - LLM integration (assume an API like OpenAI’s).
   - Data model:
     - Users
     - Games
     - Positions / Key moments
     - Player model (tags, stats).

3. **`docs/ux-flows.md`**

   - Core UX flows, especially on **mobile**:
     - Start a new game vs engine.
     - Toggle between Game Board and Analysis Board.
     - Ask “What if I play this move?”.
     - Start a post-game review.
     - Walk through key moments with explanations.
   - Wireframe-level descriptions of key screens.

4. **Initial Code Skeleton**

   - A proposed directory layout, for example:
     ```text
     mobile/
       src/
         screens/
         components/
         state/
         services/
     backend/
       src/
         api/
         engine/
         llm/
         models/
     docs/
     ```
   - Minimal placeholder files with TODOs and docstrings, not full implementation yet.
   - Clear comments indicating responsibilities of each module.

5. **Backlog / Implementation Plan**
   - A simple `docs/backlog.md` or `docs/roadmap.md` that:
     - Lists MVP milestones.
     - Orders features in a rough implementation sequence.
     - Clearly marks non-MVP items (e.g., red-team feedback / RLHF loop) as _later_.

---

## 4. Constraints and Priorities

1. **Mobile-first**

   - Prioritize mobile UX and architecture decisions.
   - Desktop/web should be considered but not lead the design.
   - Assume users are likely to play and review on phones.

2. **MVP Simplicity**

   - Focus on:
     - Dual-board interaction.
     - Clear explanations.
     - Simple, transparent mechanics.
   - Avoid over-engineering:
     - For memory, start with tagged stats and simple rules.
     - For concept retrieval, start with rule-based or lightweight mapping.

3. **Chess Engine + LLM Orchestration**

   - Design an API that:
     - Accepts a position and a user question (e.g., “Is Nf3 good?”).
     - Calls the engine to get evaluations and candidate lines.
     - Calls an LLM to generate a user-level explanation using that data.
   - Think in terms of **clear interfaces** and **separation of concerns**:
     - Engine service
     - Tutor brain (LLM service)
     - Game state service
     - Mobile app front-end

4. **Red-Team / RLHF Feature**
   - Recognize this as a powerful future idea:
     - Strong players can challenge Caïssa’s explanations and propose improvements.
     - Their feedback can be used as preference data to refine the tutor.
   - For now:
     - Document this in the roadmap.
     - Do not design or implement heavy infra for it in MVP.
     - Optionally, keep it in mind when designing data schemas so that future extensions are natural.

---

## 5. Suggested Next Steps (for You, Codex)

1. **Read `README.md` carefully** and extract initial user stories.
2. Create:
   - `docs/requirements.md`
   - `docs/architecture.md`
   - `docs/ux-flows.md`
3. Propose a **tech stack** suited for:
   - Rapid mobile development.
   - Solid backend orchestration.
4. Define an **initial directory structure** and scaffold minimal files.
5. Populate `docs/backlog.md` with:
   - MVP items.
   - Post-MVP items (including red-team/RLHF).
6. As you add files, keep them small, well-commented, and focused on clarity.

---

## 6. Style & Quality

- Prefer clear, well-structured docs over premature code complexity.
- Use straightforward, readable naming conventions.
- Document assumptions explicitly.
- Keep the focus on **teaching quality and UX**, not just engine “strength”.

---

## 7. Collaboration Ritual

- Treat every substantial artifact (each doc, architecture sketch, backlog update, or comparable deliverable) as a checkpoint.
- After you produce a draft, pause and surface it for human review before starting the next major document or implementation sweep.
- Apply this review gate even when updates feel minor; assume the user may have questions or clarifications.
- Only proceed to the next major task after the user explicitly confirms the draft is accepted or provides adjustments.

Your job is to set up Caïssa so that both humans and AI collaborators can iterate rapidly toward a real, delightful product.
