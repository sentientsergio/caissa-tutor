# Caïssa Backlog & Roadmap – Draft

_Status: Draft for review_

## 1. Guiding Themes
1. Deliver a delightful mobile human-vs-computer experience where the tutor is a trusted third-party coach on the human’s side (never the opponent).
2. Stage additional learning depth (post-game review, memory, multiplayer) once core loop is sticky.
3. Keep future RLHF/red-team feedback in mind, but do not block MVP milestones on it.

## 2. MVP Milestones (Ordered)

| ID | Milestone | Description | Exit Criteria |
| --- | --- | --- | --- |
| M1 | Foundations & Auth | Set up repo, CI, shared types, device/magic-link auth, token refresh. | Users can sign in/out, resume sessions securely. |
| M2 | Game Session Loop | Dual-board UI (light/dark mode contrast), tutor panel interactions, engine integration, takebacks per mode. | Player can complete a full game vs tutor, including what-if queries and post-move reflections. |
| M3 | Tutor Orchestrator | LLM prompt pipeline, mode-specific tone, privacy messaging, latency safeguards. | Tutor responds contextually with engine-backed insights under 5s P95. |
| M4 | Observability & Safeguards | Logging, metrics dashboards, error handling, graceful fallbacks, content filters. | On-call can monitor system health; tutor failure surfaces friendly message. |
| M5 | Session Wrap & Reflection | End-of-game banners, lightweight reflection capture, share feedback hook. | Users see wrap screen and optional reflection input; data stored for future review features. |

## 3. Post-MVP Roadmap (Backlog)
1. **Structured Post-Game Review**
   - Automated key-moment detection, guided walkthrough, PGN export.
2. **Player Memory & Pattern Surfacing**
   - Tagging engine, recurring issue alerts, personalized drill recommendations.
3. **Multiplayer + Tutor**
   - Human-vs-human games with tutor assistance (spectator or whisper modes).
4. **Push Notifications & Scheduling**
   - Lesson reminders, streaks, nudge to review after idle periods.
5. **Wireframe / Visual Refinement**
   - High-fidelity mockups for dual-board, mode selection, session wrap once tooling is ready.
6. **Red-Team Feedback / RLHF Loop**
   - Strong-player challenge flow, feedback capture, preference learning pipeline.
7. **Content Expansion**
   - Retrieval-augmented explanations referencing GM games and classical texts.
8. **Drill Generation**
   - Automatically create puzzles from user games and curated databases.

## 4. Open Backlog Questions
1. When should we prioritize offline capabilities (if ever)?
2. Do we need localized content before or after multiplayer support?
3. How will we source strong-player reviewers for the red-team phase?

---
**Next Action:** Await review/feedback. Once approved, we can proceed to scaffolding the project directories/code skeleton per AGENT instructions.
