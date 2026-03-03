# Atelier Enchanté — State Flow Definition

## Global State Variables

- currentScene
- transitionInProgress
- selectedNode
- animationActive

---

## Scene Lifecycle

### 1. Initial Load

State:
currentScene = "landing"
transitionInProgress = false
animationActive = true

LandingScene is mounted.

---

### 2. Enter Library Triggered

Event:
User clicks entry element.

State Changes:
transitionInProgress = true
animationActive = false

LandingScene fades out.
SceneManager prepares LibraryScene.

---

### 3. Library Activated

State:
currentScene = "library"
transitionInProgress = false
animationActive = true

LibraryScene mounts.
Starfield animation starts.
Interactive elements enabled.

---

### 4. Node Selected

Event:
User clicks a book/node.

State:
selectedNode = nodeId

Book animation plays.
Content panel opens.

---

### 5. Close Node

Event:
User closes panel.

State:
selectedNode = null

Panel closes.
Library remains active.

---

## Transition Rules

- No scene switch without transitionInProgress flag.
- Only SceneManager can modify currentScene.
- UI components never directly change global scene state.
- Animations stop during scene transition.
