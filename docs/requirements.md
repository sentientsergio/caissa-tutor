# Caïssa MVP Requirements (Draft)

_Status: Draft for review_

## 1. Purpose
This document translates the Caïssa vision into concrete MVP requirements. It is the baseline for architecture, UX flows, and backlog planning. Assumptions and TBDs are called out for confirmation before implementation.

## 2. Product Scope & Assumptions
- **Surfaces**: iOS and Android via a shared mobile codebase; desktop/web is deferred until the mobile MVP is stable.
- **Play context**: MVP is human-vs-tutor (engine-backed) with the dual-board interface; multiplayer and structured post-game review move to the backlog.
- **Connectivity**: Requires network access for engine + LLM orchestration; offline mode is out of scope.
- **Identity**: Lightweight account with email or device-based login; social login TBD.
- **Data retention**: Store last 100 games per user (configurable) plus aggregated stats; older history may be archived but not exposed in MVP UI.
- **Safety**: Content filtering handled by upstream LLM provider; additional heuristics TBD.
- **Tutor privacy model**: The conversational tutor sits on the player’s side only; the chess engine opponent never receives player chat history or hinted plans, and UI copy reassures the user of this separation.

## 3. Personas & Teaching Modes
| Mode | Player profile | Tone & depth | Key differentiators |
| --- | --- | --- | --- |
| **Beginner** | <800 rating, may not know all rules | Conversational, plain language, no eval scores | Emphasize legality checks, basic principles, highlight hanging pieces |
| **Improver** | 800–1800, club players | Structured reasoning, name tactical motifs, light eval cues | Prompt for candidate moves, highlight plans and pawn structures |
| **Challenger** | 1800+, serious improvers | Direct, professional, includes concrete eval deltas | Focus on critical moments, practical trade-offs, allows deeper analysis lines |

## 4. User Stories & Functional Notes
Stories follow "As a `<mode>` player, I want `<goal>` so that `<benefit>`" and each is paired with the acceptance notes needed for implementation.

### 4.1 Playing a Game (MVP)
1. **As any player, I want to start a tutor-guided game by picking mode/time/color so that the experience matches my goals.**
   - Provide presets for Beginner/Improver/Challenger, plus untimed mode; persist last choice per user.
2. **As any player, I want a clear dual-board interface so that I can flip between the active game and exploratory analysis.**
   - Game Board always reflects official moves; Analysis Board mirrors current position but only updates when user requests analysis.
3. **As a Beginner, I want optional tutor prompts during my turn so that I feel supported without being overwhelmed.**
   - Show hint button; if tapped, tutor offers gentle reminders (e.g., "Consider developing your knights").
4. **As any player, I want confirmation that my moves are legal and states like check/checkmate are obvious so that I avoid confusion.**
   - Enforce legality, highlight last moves, and surface end-of-game states loudly.
5. **As any player, I want confidence that the engine opponent is thinking independently from the tutor so that I can speak freely.**
   - Visual cues show "Tutor listening" vs "Engine thinking"; tutor chat explicitly states it will never leak intentions.
6. **As a Beginner or Improver, I may need an occasional takeback so that I can correct accidental blunders.**
   - Allow one-ply takebacks while it is still the player’s turn; Challenger mode keeps this off by default.

### 4.2 Asking for Move Explanations (MVP)
1. **As any player, I want to ask the tutor about a candidate move before playing it so that I can understand risks.**
   - Analysis Board accepts drag-and-drop "what if" lines; tutor responds with eval deltas and motifs.
2. **As any player, I want to discuss the new position right after the engine moves so that I can plan my reply.**
   - Tutor proactively offers a summary once the opponent (engine) move lands; conversation is paused while the engine is calculating to avoid interruptions.
3. **As any player, I want to reflect on the move I just made without breaking the flow so that I can learn sequentially.**
   - "Help me review my last move" becomes available after the engine replies; tutor comments once the board is stable again.
4. **As any player, I want quick responses even if deep analysis takes time so that I stay engaged.**
   - Provide immediate acknowledgement (<500ms) and allow cancel if processing exceeds 5 seconds.
5. **As a Beginner, I want responses in plain language with at most one alternative line so that I am not overwhelmed.**
   - Cap suggestions to 1–2 in Beginner mode; Improver/Challenger can see up to 3.

### 4.3 Account / Profile Basics (MVP-supporting)
1. **As any player, I want a lightweight profile so that my preferred mode and basic stats persist across sessions.**
   - Store name/alias, preferred mode, games played, and most recent coaching note.
2. **As any player, I want an easy sign-in path so that I can quickly recover my tutor history.**
   - Support email magic link or device-based account creation; expose a reset option if privacy concerns arise.
3. **As any player, I want to opt into notifications (later) so that the tutor can remind me to practice.**
   - Capture preference now; delivery may ship post-MVP.

### 4.4 Backlog User Stories (Post-MVP)
1. **Post-game review**: As any player, I want Caïssa to walk me through key moments after a game so that I can internalize lessons.
2. **Player memory model**: As any player, I want recurring patterns highlighted across games so that I see trends.
3. **Multiplayer / human vs human with tutor**: As an Improver, I want the tutor present while facing humans so that I can learn in social games.
4. **Export & sharing**: As any player, I want annotated PGNs for sharing or deeper study so that I can continue learning elsewhere.

## 5. Non-Functional Requirements
- **Performance**: UI interactions under 16ms/frame; analysis requests acknowledge within 500ms even if full answer takes longer.
- **Reliability**: If engine/LLM call fails, present friendly fallback explaining the issue and offer retry.
- **Observability**: Log latency, error codes, and tag distributions to support iteration.
- **Privacy**: Store personal data encrypted at rest; limit retention to stated scope.

## 6. Open Questions / Decisions Needed
1. Preferred authentication method (email magic link vs device-based local account)?
2. Do we need offline puzzles or is online-only acceptable for MVP launch?
3. How strict should the takeback policy be in Beginner/Improver modes?
4. Any regulatory or COPPA-like constraints because of younger players?
5. Are push notifications a launch requirement or can they slip to post-MVP?

---
**Next Action:** Await product review/feedback. Once approved, this doc becomes the baseline for architecture and UX deliverables per our collaboration ritual.
