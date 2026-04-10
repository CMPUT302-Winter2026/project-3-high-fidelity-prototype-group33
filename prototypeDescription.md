# Prototype Description: Vocabulary Explorer

## Purpose and Scope
`vocabulary-explorer.html` is a high-fidelity, single-file interactive prototype for the ALTLab Plains Cree vocabulary learning concept. It demonstrates both novice and expert learning flows through a Wizard-of-Oz style interaction model (simulated behavior, no backend required).

This document captures:
- what the prototype is meant to show,
- how advanced interactive features are expected to work,
- which usability-driven changes were applied from the most recent evaluation,
- and what Wizard controls are available to run scripted sessions.

## Users and Primary Goals
- **Novice learners:** find words quickly, hear pronunciation, and save words.
- **Teachers / lesson planners:** browse words by theme and curate useful vocabulary.
- **Expert / lexicography users:** inspect grammatical detail and semantic relations through progressive disclosure.

## Core Screens and Flows
- **Home:** two navigation paths:
  - directed lookup (search bar),
  - exploratory lookup (thematic tiles).
- **Search Results:** multiple candidate entries for a query, with audio and bookmark actions per row.
- **Map (Semantic View):** central concept plus related satellite nodes; selecting a node updates summary details.
- **Word Entry:** pronunciation, gloss, related words, map shortcut, and save action.
- **My Words:** saved vocabulary list with quick access to entry view.
- **Settings:** Expert Mode toggle for progressive disclosure.

## Advanced Interactive Features (Expected Behavior)
- **Dual-path navigation:** users can either type directly or browse by theme, matching discovery and lookup behavior.
- **Immediate pronunciation affordance:** speaker/play actions are visible where users need them.
- **Low-friction saving:** bookmark is available directly in search rows and in full word entry.
- **Feedback loops:** toast confirmation appears after save and key actions.
- **Progressive disclosure:** expert linguistic metadata is hidden by default and revealed only in Expert Mode.
- **Semantic exploration:** map allows tapping related nodes and then opening full entries.

## Changes Implemented from Latest Evaluation (M4B)
The most recent usability report identified two major issues: bookmark discoverability and uncertainty when selecting among multiple search results. The current prototype reflects the recommended fixes:

1. **Bookmark icon added to each search result row**  
   Users can save without entering the full detail page.
2. **Save confirmation toast added**  
   Displays `Saved to My Words` after bookmarking.
3. **Saved-list navigation clarified**  
   Bottom navigation uses labeled `My Words` tab.
4. **Word-class badges added (Expert Mode)**  
   Shows labels such as `VAI`, `NA`, `PV` to support confident selection.
5. **Recommended result indicator added**  
   Top/most suitable entry can be marked with `Recommended`.
6. **Search intent clarified in placeholder**  
   Uses text indicating search is for specific-word lookup.

## Wizard-of-Oz Control Stubs
To support facilitated demonstrations or moderated tests, `vocabulary-explorer.html` now exposes global stubs:

- `window.WizardControls.goToPane(name, arg)`
- `window.WizardControls.openWord(cree)`
- `window.WizardControls.setSearchQuery(query, resultCount)`
- `window.WizardControls.setMapSelection(cree, gloss)`
- `window.WizardControls.toggleExpert(on)`
- `window.WizardControls.injectSavedWords(words)`
- `window.WizardControls.simulateBookmark(cree, gloss, tag)`
- `window.WizardControls.triggerToast(text)`
- `window.WizardControls.playPronunciation()`
- `window.WizardControls.resetDemoState()`

### Example Wizard usage (browser console)
```js
WizardControls.goToPane('search');
WizardControls.setSearchQuery('blue', 5);
WizardControls.simulateBookmark('sîpihkwâw', 'it is blue', 'color');
WizardControls.toggleExpert(true);
WizardControls.goToPane('mywords');
```

## What Is Simulated vs. Real
- **Simulated:** search indexing, semantic graph logic, pronunciation audio engine, persistence backend.
- **Real in prototype context:** navigation, UI state transitions, toast feedback, list rendering, and interactive controls for usability testing.

## Known Limitations
- Data is static and intentionally lightweight.
- `playAudio` is a feedback stub (toast + animation), not actual audio playback.
- Search relevance/ranking is represented visually, not algorithmically.
- Prototype emphasizes interaction validity over production architecture.

## Recommended Next Iteration
- Connect search and word data to structured JSON or API responses.
- Replace audio stub with actual Cree pronunciation clips.
- Add first-use onboarding hint for search vs. browse behavior.
- Add quick-entry path to `My Words` after save (toast action link).
- Expand quiz/self-test from placeholder into an interactive learning loop.
