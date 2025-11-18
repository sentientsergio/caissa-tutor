<!-- Banner -->
<p align="center">
  <img src="assets/logo.png" alt="Caïssa – The Lifelong Chess Tutor" width="420">
</p>

<h1 align="center">Caïssa – The Lifelong Chess Tutor</h1>

<p align="center">
  Where chess wisdom, engines, and memory come together to teach every player.
</p>

---

## What is Caïssa?

**Caïssa** is an AI-powered chess tutor designed to _end the gatekeeping of chess mastery_.  
It’s not just an engine, not just a tactics app, and not just a book. It’s a **personal coach** that:

- Plays games with you
- Explains your ideas in natural language
- Walks through variations on an analysis board
- Reviews your games afterward
- Remembers your recurring mistakes and patterns over time

The long-term vision is a **lifelong chess mentor** that grows with the player, working just as well for a total beginner as for a serious improver trying to challenge strong engines.

This repo now contains the outcomes of the initial design sprint for Caïssa’s **MVP**. For detailed specs, architecture, UX flows, and roadmap, see the documents referenced near the end of this README.

---

## Core Concept

### Dual-Board Experience

Caïssa’s signature UX is a **dual-board interface**:

- **Game Board** – where the real game is played (vs engine or human).
- **Analysis Board** – a sandbox where the tutor can:
  - Show “what if” lines
  - Compare candidate moves
  - Illustrate tactical motifs
  - Demonstrate plans from grandmaster games
  - Revisit past mistakes in similar positions

This separation keeps competitive play clean while still enabling rich, interactive teaching.

---

## Teaching Modes (MVP Scope)

The MVP should support three teaching modes, all powered by the same core engine + LLM stack, but with different depth and tone.

1. **Beginner Mode**

   - Audience: players who may not fully know the rules.
   - Focus:
     - Simple principles: center control, development, king safety.
     - Plain language, no eval bars, no engine jargon.
     - Basic “why this move?” explanations and safety checks.
   - Goal: make chess feel approachable, not intimidating.

2. **Improver Mode**

   - Audience: roughly 800–1800 rating (flexible, not strict).
   - Focus:
     - Candidate move thinking (“What 2–3 moves did you consider?”).
     - Tactical motifs (forks, pins, discovered attacks, loose pieces).
     - Positional concepts (pawn structures, weak squares, open files, piece activity).
   - Uses:
     - Engine analysis in the background.
     - Classical ideas (e.g., Nimzowitsch’s _My System_ and other strategic texts) as conceptual context.
   - Goal: help users understand _plans_, not just single best moves.

3. **Challenger Mode**
   - Audience: stronger improvers trying to play vs strong engines or significantly improve.
   - Focus:
     - Critical moments, practical decisions, trade-offs between sharp and safe lines.
     - Deeper lines on the analysis board when requested.
     - “Professional” solutions that balance complexity vs reliability.
   - Goal: serve as a strong training partner, not just an evaluator.

---

## Current MVP Scope

The first build focuses solely on **human vs computer** play where the tutor is a trusted third party sitting on the human side. The engine opponent never sees the tutor conversation—players can plan moves in private and only commit when ready. Shipping goals:

- Mobile-first dual-board experience: a light-mode tournament board for live play plus a contrasting dark-mode analysis panel with chat, scrubbing, and shortcuts like “Position?” or “Best moves?”.
- Mode-specific tone (Beginner / Improver / Challenger) driven by the tutor orchestrator and Stockfish-backed analysis.
- Lightweight account layer (device or magic link) so users can resume sessions.
- Session wrap banner with optional reflection input (full post-game review is deferred to the roadmap).

Player memory, multiplayer, and structured reviews remain critical but are tracked as post-MVP milestones.

---

## Roadmap: Later (Non-MVP) Ideas

These ideas are important but **not required for the MVP**. They should be treated as expansion points:

- **Advanced “Red-Team” Feedback from Strong Players**

  - Strong users can challenge Caïssa’s advice, provide corrected explanations and lines.
  - Their feedback can be used to refine the tutor via RLHF / preference learning.
  - This is a **later-phase feature**, not part of the initial release.

- **Richer Retrieval from Texts & GM Games**

  - Deeper integration of classical literature and curated grandmaster games.
  - Dynamic retrieval of relevant examples based on structures and motifs.

- **Drill Generation at Scale**
  - Automatic creation of personalized problem sets sourced from the user’s own games and similar positions in databases.

---

## Platform & Viral Potential

**Initial focus should be mobile**, with desktop/web as a parallel or follow-up surface:

- Mobile is critical for virality and stickiness:
  - Quick game + review loops on the go.
  - Push notifications for lesson reminders and reviews.
  - Easy sharing of positions and insights.

Recommended direction:

- **Mobile-first UX**:
  - Native or cross-platform (e.g., React Native or Flutter) for iOS and Android.
  - Clean, thumb-friendly dual-board interface.
- **Backend & APIs**:
  - A service layer that:
    - Manages users, games, and sessions.
    - Orchestrates engine analysis + LLM explanations.
    - Stores memory and player models.

Desktop/web can reuse much of the same backend and conceptual model, but **mobile should not be an afterthought**.

---

## Status

- ✅ Design sprint complete: requirements, architecture, UX flows, and backlog captured in `/docs`.
- 🚧 Implementation not started: next up is scaffolding mobile + backend skeletons per `AGENT.md`.

## Design Artifacts Index

| Area | File |
| --- | --- |
| Detailed MVP requirements & user stories | [`docs/requirements.md`](docs/requirements.md) |
| System architecture, stack, data model | [`docs/architecture.md`](docs/architecture.md) |
| Mobile UX flows & wireframe prompts | [`docs/ux-flows.md`](docs/ux-flows.md) |
| Backlog & roadmap (MVP → post-MVP) | [`docs/backlog.md`](docs/backlog.md) |
| Agent collaboration ritual & instructions | [`AGENT.md`](AGENT.md) |

Refer to those documents for authoritative guidance as we move into implementation. Contributions—human or AI—should treat this README as the high-level narrative and the `/docs` set as the source of truth for specifics.
