# Archived initial plan

Archived on 7 November 2026 when the owner selected the DIY route and the current detailed wireless design was documented.

**Historical reference only.** Board choice, sensing scope, budget and work order below are superseded by [the current plan](../PLAN.md). The original wording follows.

---

# Hand Glove — Plan

**Goal**  
Build a real sensor glove that fixes the main problem of webcam hand tracking: missed or wrong clicks when fingers hide each other.

The glove reads fingers and hand rotation directly. A live 3D hand on screen copies the real hand. It works with Hand Graph (https://hand-graph.vercel.app).

**Important truth**  
A glove knows finger bend and hand rotation. It does **not** know where the hand is in the room.  
Pointer = IMU air-mouse. Webcam can still help with position when it can see the hand (sensor fusion later).

---

## Two versions

### CHEAP v1 (~₦40k target)
- ESP32 board with BLE
- One IMU (MPU6050 or better) for air-mouse + rotation
- Copper tape / conductive thread contact pads on thumb, index, middle tips
  - Thumb–index contact = left click
  - Thumb–middle contact = right click
- Small vibration motor that buzzes on click
- Powered by USB or small battery
- No flex sensors → 3D hand can only show open / closed from contacts + IMU, not per-finger bend

### FULL v2
- Everything in v1
- 5 flex (bend) sensors — one per finger
- Better IMU (BNO085 preferred)
- LiPo battery + charger board + on/off switch
- 3D hand bends every finger correctly
- Can detect fist, two-fingers, etc. without camera

---

## Repo structure

```
hand-glove/
├── docs/
│   ├── PLAN.md          ← this file
│   ├── BOM.md           ← shopping list with prices & links
│   ├── BUILD.md         ← step-by-step assembly
│   ├── WHO-BUILDS.md    ← Lagos people/places that can assemble it
│   ├── PROTOCOL.md      ← BLE packet format + UUIDs
│   ├── SAFETY.md        ← LiPo + soldering safety
│   └── img/             ← photos, diagrams, wiring SVGs
├── firmware/            ← PlatformIO / Arduino project for ESP32
│   └── (v1 and v2 controlled by #define)
├── web/
│   ├── glove.js         ← Web Bluetooth driver
│   ├── hand3d.js        ← Three.js live 3D hand
│   ├── simulator.html   ← test without hardware
│   └── calibration      ← open/fist + IMU zero
└── tests/               ← Playwright tests against the simulator
```

---

## Work order (what we do next)

1. **This PLAN.md** — done. You read it and say OK or change it.
2. **Pictures & diagrams** (Step 2)
   - Realistic picture of finished glove
   - Labelled top + palm views
   - Exact wiring diagram + pin table for chosen ESP32 board
3. **BOM.md** (Step 3) — every part, Lagos-first shops, prices checked on the web, totals for v1 and v2
4. **WHO-BUILDS.md** (Step 4) — real Lagos makers / technicians / tailor + job brief + labour price
5. **PROTOCOL.md + firmware skeleton + web/glove.js + hand3d.js + simulator** (Step 5)
   - Software works **before** the glove exists (simulator first)
6. **Integration PR** into hand-graph so the glove becomes another input source next to the webcam

---

## Chosen board (provisional)

**ESP32-C3 SuperMini** or **ESP32-S3** (final choice after BOM check).  
Reasons: small, BLE 5, enough ADC pins that still work while Bluetooth is on, cheap in Lagos markets.

Pin table and exact model will be fixed in the wiring diagram.

---

## Success criteria

- v1 glove can left-click and right-click by real electrical contact (no guessing).
- IMU moves a pointer on screen like a presentation clicker.
- Vibration motor buzzes on successful click.
- Live 3D hand appears and rotates with the real hand.
- Everything can be tested with the web simulator (no hardware needed).
- Hand Graph Practice page scores glove use the same way it scores camera use.
- Total parts cost for v1 stays near ₦40k if possible.

---

## Next action

You: read this plan. Tell me any change you want.  
Then I produce the pictures and diagrams (Step 2) and put them in `/docs/img`.
