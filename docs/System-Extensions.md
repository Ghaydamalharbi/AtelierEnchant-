# Atelier Enchanté — System Extensions

This document defines modular extensions that integrate with the core scene-based SPA architecture without violating architectural constraints.

These modules are optional in Phase 1 but structurally reserved from the beginning.

---

# 1. Audio Layer

## Purpose

Provide immersive soundscapes without impacting rendering performance or state integrity.

## Controller

AudioController

## State Extensions

- audioEnabled
- currentSoundTheme
- soundVolume

## Sound Themes

- "fairy" (LandingScene)
- "library" (LibraryScene)
- "silent"

## Rules

- Audio starts only after user interaction (browser policy compliance).
- SceneManager triggers theme changes.
- AudioController never modifies scene state.
- Sound loops must be controlled and memory-safe.

## Non-Goals (Phase 1)

- No complex sound engine
- No dynamic mixing
- No spatial audio

---

# 2. AI Agent Layer

## Purpose

Represent an interactive intelligent entity within the LibraryScene.

## Controller

AIController

## State Extensions

- aiActive
- aiMode ("idle" | "wise" | "lazy" | "responding")
- aiInteractionState ("listening" | "processing" | "replying")

## Rules

- AI cannot operate during scene transitions.
- AI responses pass through controller logic before UI rendering.
- AI does not directly mutate global scene state.
- Interaction must be interrupt-safe.

## Future Direction

- API-based LLM integration
- Adaptive personality modes
- Context-aware responses using interactionHistory

---

# 3. User Context Layer

## Purpose

Enable personalization and future scalability without authentication dependency.

## Controller

UserContextManager

## State Extensions

- userSessionId
- userPreferences
- interactionHistory

## userPreferences

- themePreference
- soundPreference
- reducedMotion

## interactionHistory

- visitedNodes
- timeInScene
- aiInteractionsCount

## Rules

- Stored locally (Phase 1)
- No backend persistence yet
- Must not affect performance loop

---

# Integration Philosophy

Core Scene System remains isolated.

Extensions communicate via:

- StateStore (read-only where possible)
- Event-based triggers
- Controlled controller interfaces

No extension is allowed to directly override core scene logic.

---

# Architectural Intent

The system is designed to evolve without restructuring the foundation.

All extensions are modular, replaceable, and non-invasive.
