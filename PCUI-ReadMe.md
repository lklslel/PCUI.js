# PCUI.js

**PCUI.js** is a low-level, FSM-driven input and UI interaction engine designed for
canvas-based applications.  
It bypasses browser default input handling to provide **deterministic, multi-pointer,
multi-language, and IME-aware input processing**.

PCUI.js is built for scenarios where correctness, predictability, and fine-grained
control over input behavior are required.

---

## ✨ Key Features

### Keyboard & IME Input
- Custom FSM-based keyboard input handling
- Explicit modifier key tracking via bitmask (Shift / Ctrl / Alt / CapsLock / Meta)
- Built-in IME composition support:
  - English
  - Korean
  - Vietnamese
- Deterministic composition (`preedit` / `commit`) control
- Chromium / V8 switch–case optimization safe (single return point design)

### Pointer / Mouse / Touch Input
- Unified PointerEvent-based architecture
- Slot-based multi-pointer handling (PSlot)
- Independent FSM per pointer slot
- Bitmask-driven state tracking (Down / Move / Drag / Hover)
- Multi-touch safe drag and focus handling
- Hover / tooltip suppression during drag

### Architecture
- FSM + RUN flag control flow (no deep nested conditionals)
- Slot-based state isolation
- Bitmask-driven event classification
- Rendering-loop–synchronized input updates
- Designed to mitigate browser event quirks and race conditions

---

## 🧠 Core Design Principles

- **Drag is a mode, not an event**
- **One pointer → one slot → one focus owner**
- No implicit browser behavior
- No hidden global state for interaction
- Deterministic execution per frame
- Input handling is separated from rendering

---

## 🧪 Demo

Live demo (GitHub Pages):

👉 **https://lklslel.github.io/PCUI.js/PCUI_TEST.html**

The demo showcases:
- Multiple `window_ui` instances
- Drag via bar area
- Multi-pointer / multi-touch dragging
- Slot-based focus isolation
- Canvas-based rendering with custom input handling

---

## 📁 Project Structure (Conceptual)

```text
PCUI.js
├─ input/
│  ├─ keyboard_ime_fsm.js
│  ├─ pointer_slot.js
│  └─ event_bitmask.js
├─ ui/
│  ├─ window_ui.js
│  └─ bar_ui.js
├─ core/
│  ├─ fsm_runner.js
│  └─ render_loop.js
├─ PCUI_TEST.html
└─ README.md
````