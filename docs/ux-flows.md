# Caïssa UX Flows – Draft

_Status: Draft for review_

## 1. Goals
- Visualize the key mobile-first interactions: starting a tutor-guided game, toggling boards, asking for analysis, and wrapping up a session.
- Provide narrative flow descriptions plus prompt-ready guidance for external wireframe generation.
- Keep flows limited to the MVP scope (human vs tutor). Post-game review and multiplayer live in backlog.

## 2. Flow Summaries

### 2.1 Launch & Session Setup
1. **Splash / Auth Check**
   - App verifies stored token; if absent, presents magic-link/device sign-in.
2. **Home / Continue Card**
   - Shows "Resume last session" if one is active, otherwise CTA: "Start Tutor Game".
3. **Mode & Time Selection**
   - Sheet with Beginner / Improver / Challenger cards (icons + tone summary) and time controls (15+10, 10+0, Untimed). Color picker below.
4. **Confirmation Screen**
   - Recap of choices + reassurance copy (“Tutor stays private. Engine does not see this chat.”) before entering dual-board view.

### 2.2 Dual-Board Interaction (Core Play Loop)
1. **Game Board View (Full Screen)**
   - Occupies entire screen; plays like a standard engine match with clocks and move list. Zero tutor UI beyond a small "Tutor" tab at the bottom, reinforcing that you can play distraction-free if desired.
2. **Summon Tutor / Analysis Board**
   - Tap the bottom "Tutor" tab; the screen slides up half-height analysis panel with a mirrored board flush to the top of the panel and a chat area beneath it. Game board remains paused in background.
3. **Timeline Scrubber**
   - Back/forward chevrons (and optional slider) let users jump to any move in the game. Current cursor is synced with both boards; users can ask about past positions, not just the latest.
4. **Shortcut Prompts**
   - Chat composer includes quick chips such as "Position?", "Best moves?", and "Plan for me" that auto-fill natural-language questions scoped to the board cursor and side to move.
5. **Ask "What if?"**
   - User either drags a hypothetical move on the analysis board or types a free-form query; pressing send dispatches the context to the tutor.
6. **Tutor Response**
   - Chat bubbles return with summary, eval delta, motif chips, and optional inline buttons to project recommended lines onto the analysis board. Conversation history stays in this panel so it never interrupts the game board experience.
7. **Return to Game Board**
   - Swipe the panel down or tap "Back to Game"; the analysis board disappears and players continue normally. The tutor tab subtly pulses when new advice is available after the engine moves.
8. **Visual Theme Contrast**
   - Game Board uses light mode with wood-textured pieces/board reminiscent of tournament sets. Analysis panel switches to a sleek dark mode with flat black/white pieces on light-gray squares, visually cueing that you’re in a sandbox.
9. **Panel Height**
   - When expanded, the analysis panel covers roughly 70% of the screen—enough to keep the board large while leaving space for chat controls at the bottom without feeling cramped.

### 2.3 Opponent Move & Post-Move Reflection
1. **Engine Move Notification**
   - Subtle vibration + highlight on Game Board; tutor chip reads “Let’s discuss?”
2. **Position Summary Prompt**
   - User taps chip; chat opens with quick summary (“They targeted your king side… wanna counter?”).
3. **Plan Reply**
   - User either drags next move on Analysis Board or types a question.
4. **Post-Move Review (Optional)**
   - After user commits move and engine replies, button “Review my last move” becomes active. Tutor summarizes when pressed.

### 2.4 Session Wrap (MVP)
1. **Game End State**
   - Banner (Win/Loss/Draw) + final evaluation summary.
2. **Quick Reflection Prompt**
   - Short text input: “What was the key idea you learned?” (optional, stored locally for future review features).
3. **Next Actions**
   - Buttons: “Start new game” or “Share feedback”. Link to backlog features (“Full review coming soon”).

## 3. Wireframe Prompt Suggestions
_Status: Backlogged_. Current gen tools (e.g., GPT-4.1) could not deliver reliable wireframes, so these prompts are placeholders for when higher-fidelity tooling is available closer to implementation.

If you are generating mockups externally (e.g., GPT-5.1 image generator), use prompts like:

1. **Dual-Board Screen**
   - _"Mobile chess tutor app showing a light-mode wooden tournament board for the main game. A 'Tutor' tab at the bottom slides up a 70% height dark-mode analysis panel with a monochrome board, move scrubber, and chat area with shortcut chips ('Position?', 'Best moves?'). Include privacy reassurance text."_
2. **Mode Selection Sheet**
   - _"Mobile modal sheet with three cards labeled Beginner, Improver, Challenger, each with icon and tone description, plus time-control pills and a confirmation button."_
3. **Engine Move Summary**
   - _"Mobile chess app toast showing engine move highlight and a tutor prompt chip inviting discussion, with a collapsed chat preview."_
4. **Session Wrap Banner**
   - _"Mobile screen showing game result banner, short reflection input, and CTA buttons for 'Start new game' and 'Share feedback', with mention of upcoming post-game review feature."_

Feel free to request more specific prompts (different orientations, dark mode, etc.) and I will tailor them.

---
**Next Action:** Await feedback; once approved we proceed to backlog/roadmap doc.
