# ⚙️ Echo Chip: Mechanics Bible

This document codifies the gameplay systems, movement parameters, ability logic, puzzle architecture, and combat economy of *Echo Chip: 8-Bit Hero*. It serves as the canonical reference for developers, designers, and systems thinkers building or extending the game.

---

## 🧠 Design Philosophy

Echo Chip is built on sovereign iteration and mythic modularity. Every mechanic is a metaphor. Every system is designed for inheritance, remixability, and emergent gameplay.

---

## 🚶 Movement Systems

- **Ground Speed**: 180 px/s  
- **Air Control**: 65% of ground movement  
- **Jump Logic**: Coyote time (0.15s), jump buffer (0.1s)  
- **Wall Climbing**: Stamina-based, upgradeable with Magnetic Grip  
- **Advanced Traversal**: Wall jumps, double jumps, air dashes, wall running

---

## 🔊 Ability Systems

### Sonic Wave  

- Shatters objects, damages enemies, pushes projectiles  
- Cooldown: 1.2s | Range: 300px | Damage: 15–25 HP  
- Unlocks: Push impulse, combo resonance, frequency mastery

### Echolocation  

- Reveals hidden paths and objects  
- Energy drain: 5 units/sec | Radius: 600px | Pulse: every 1.5s

### Magnetism  

- Push/pull objects, swing from grapple points, polarity-based puzzles  
- Range: 450–550px | Force: 280 px/s² | Energy cost: 8 units/sec  
- Unlocks: Multi-grapple, polarity switching, field manipulation

---

## 🧩 Puzzle Systems

- **Environmental**: Shatterable walls, magnetic crates, resonance crystals  
- **Frequency Matching**: 5 Hz bands, ±5% tolerance  
- **Timed Sequences**: 2–8s windows, visual cues, reset logic  
- **Physics-Based**: Weight classes, friction values, force thresholds

---

## ⚔️ Combat Systems

- **Enemy Archetypes**:
  - Red (Explosive): Charge + AoE
  - Blue (Energy Drain): Radius-based drain
  - Green (Agile): Fast melee, wall climbing
  - Yellow (Ranged): Projectile attacks, cover usage

- **Boss Design**: Multi-phase encounters with puzzle-combat hybrids  
- **Combat Economy**: Damage scaling, spawn logic, environmental synergy

---

## 🌱 Progression Systems

- **Skill Tree**: Sonic, Magnetic, Movement branches (5 tiers each)  
- **XP Sources**: Combat, puzzles, exploration, rescues  
- **Upgrade Costs**: Tiered from 100 to 1000 XP

---

## 🧬 Procedural Generation

- **Chunk Types**: Platforming (60%), Puzzle (25%), Combat (15%)  
- **Rules**: Max 3 same-type chunks, difficulty gradient, theme consistency  
- **Dynamic Elements**: Platform patterns, enemy placement, puzzle variety

---

## 🛠️ Technical Parameters

- **Physics**: Gravity (1800 px/s²), friction (0.92), elasticity (0.3–0.8)  
- **Optimization**: Object pooling, LOD, chunk preloading, render layers  
- **Performance Target**: 60 FPS across mid-range systems

---

## 🎮 Control Scheme

- **Default Bindings**:  
  - Movement: Arrow Keys / Left Stick  
  - Jump: Z / A  
  - Sonic Wave: X / X  
  - Magnetism: C / B  
  - Echolocation: V / Y  
  - Polarity Switch: Shift / LB  
  - Interact: E / RB

- **Input Handling**: Buffering, rollover, analog sensitivity

---

## ♿ Accessibility

- **Visual**: Colorblind modes, high contrast, UI scaling  
- **Difficulty**: Puzzle hints, combat scaling, platform assistance  
- **Controls**: Full remapping, sensitivity tuning, dynamic prompts

---

## 📜 Version History

| Version | Highlights                          |
|---------|-------------------------------------|
| 1.0     | Core movement + ability systems     |
| 1.1     | Enemy AI + combat logic             |
| 1.2     | Puzzle architecture + generation    |
| 1.3     | Skill tree + progression economy    |
| 1.4     | Optimization + accessibility polish |

---

> “Great mechanics feel invisible—players should feel powerful, not think about inputs.”
