# Atelier Enchanté — Architecture Definition

## System Type

Single Page Application (SPA)  
Scene-Based Rendering Model

---

## High-Level Structure

App
 ├── SceneManager
 │     ├── LandingScene
 │     └── LibraryScene
 ├── StateStore
 ├── AnimationEngine
 ├── UIComponents
 └── ContentLayer

---

## Core Architectural Principles

1. Architecture before aesthetics  
2. Performance is a feature  
3. Explicit state management  
4. Scalable modular structure  
5. Documented decision-making  

---

## Scene Model

### LandingScene
- Soft animated background
- Entry trigger
- Minimal interaction

### LibraryScene
- Starfield canvas layer
- Pixel library structure
- AI character sprite
- Clickable knowledge nodes

---

## State Model

Global State:

- currentScene
- transitionInProgress
- selectedNode
- animationActive

State rules:
- Only one active scene at a time
- Transitions are controlled centrally
- No implicit DOM-driven logic

---

## Rendering Strategy

- requestAnimationFrame for animations
- Canvas layer for starfield
- Minimal DOM mutation
- Controlled re-render logic

---

## Performance Constraints

- Stable 60fps target
- Limited particle count
- No unnecessary loops
- Lightweight initial load

---

## Scalability Considerations

- Modular scene addition
- Separable content layer (JSON-ready)
- Future AI integration point
- Clean separation of rendering and logic

---

## Non-Goals (Phase 1)

- No backend integration
- No authentication system
- No external API dependency
- No premature optimization beyond defined constraints

