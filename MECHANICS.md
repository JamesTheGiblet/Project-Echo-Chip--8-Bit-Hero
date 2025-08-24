# MECHANICS.md - Echo Chip: Game Systems & Mechanics Bible

## Overview
This document details all gameplay systems, mechanics, and technical implementations for Echo Chip: 8-Bit Hero. It serves as the primary reference for developers, designers, and playtesters to maintain consistency across all gameplay elements.

## Core Movement Systems

### Basic Movement Parameters
| Parameter | Value | Description |
|-----------|-------|-------------|
| Base Move Speed | 180 px/s | Horizontal movement on ground |
| Air Control | 0.65 | Reduction factor for aerial movement |
| Base Jump Velocity | -380 px/s | Initial upward velocity |
| Max Fall Speed | 600 px/s | Terminal velocity |
| Coyote Time | 0.15s | Time window after leaving ledge to still jump |
| Jump Buffer | 0.1s | Time window before landing to queue jump |

### Wall Climbing Mechanics
- **Surfaces**: Designated climbable walls (visual indicator: vertical energy conduits)
- **Climb Speed**: 120 px/s vertical movement
- **Stamina System**: 5-second climb limit, 3-second recharge
- **Wall Jump**: Kick-off with horizontal velocity +300 px/s, vertical +250 px/s
- **Upgrades**: 
  - **Magnetic Grip**: Unlimited climb stamina
  - **Ionic Traction**: Climb icy surfaces (25% speed reduction)

## Ability Systems

### Sonic Wave Ability
**Primary Function**: Shatter vulnerable objects and enemies
- **Cooldown**: 1.2 seconds
- **Range**: 300 pixels cone-shaped emission
- **Damage**: 15 HP to vulnerable enemies
- **Visual**: Blue wave emission with screen shake (0.1s duration)
- **Audio**: High-frequency burst with glass break SFX

**Secondary Function**: Push (unlocked via skill tree)
- **Force**: 400 px/s impulse to objects
- **Object Mass Limit**: 3.0 units (affects push distance)
- **Special**: Can redirect certain projectiles

### Echolocation Ability
**Activation**: Toggle ability (energy drain: 5 units/second)
- **Radius**: 600 pixels circular pulse
- **Pulse Frequency**: Every 1.5 seconds
- **Reveal Duration**: 4 seconds for hidden objects/paths
- **Visual**: Concentric blue circles with fading opacity
- **Audio**: Subtle ping with pitch indicating object density

### Magnetic Abilities

**Basic Magnetism (Push/Pull)**
- **Range**: 450 pixels
- **Force**: 280 px/s² acceleration
- **Mass Limit**: 5.0 units
- **Energy Cost**: 8 units per second of activation
- **Visual**: Orange energy tether between Chip and object

**Magnetic Swing**
- **Grapple Range**: 550 pixels
- **Swing Physics**: Pendulum motion with adjustable length
- **Release Velocity**: Conservation of angular momentum
- **Upgrade**: **Multi-Grapple** - Connect to 2 points simultaneously

**Polarity Switching**
- **Cooldown**: 3 seconds between switches
- **Positive Pole**: Repels same-colored objects/enemies
- **Negative Pole**: Attracts opposite-colored objects
- **Visual**: Chip's chassis changes color (blue/red)

## Puzzle Mechanics

### Environmental Interaction System

**Shatterable Objects**
- **Glass Panels**: 1 Sonic Wave hit to destroy
- **Cracked Walls**: 3 Sonic Wave hits (visual cracking progression)
- **Resonance Crystals**: Shatters after receiving correct frequency

**Magnetic Objects**
- **Ferrous Crates**: Can be pushed/pulled, mass: 2.0 units
- **Magnetic Plates**: Activate switches when placed correctly
- **Floating Platforms**: Levitate when polarized correctly

**Energy Systems**
- **Conductivity**: Certain materials chain energy transfers
- **Resonance Fields**: Require specific frequency matching
- **Power Nodes**: Must be activated in correct sequence

### Puzzle Types & Parameters

**Frequency Matching Puzzles**
- **Frequency Range**: 5 available frequencies (Hz: 110, 220, 440, 880, 1760)
- **Tolerance**: ±5% frequency accuracy required
- **Visual**: Oscilloscope-style display when active

**Timed Sequence Puzzles**
- **Time Window**: 2-8 second intervals based on difficulty
- **Visual Cues**: Pulsing lights or moving indicators
- **Failure State**: Reset sequence after 1.5 seconds of inactivity

**Physics-Based Puzzles**
- **Object Weight Classes**: Light (1.0), Medium (3.0), Heavy (7.0)
- **Force Requirements**: Minimum force to move objects varies
- **Friction Values**: Different surface types affect movement

## Combat Systems

### Enemy Archetypes

**Red (Explosive) Enemies**
- **Health**: 20 HP
- **Attack**: Contact explosion (25 damage in 150px radius)
- **Behavior**: Charge directly at player
- **Weakness**: Sonic Wave from distance

**Blue (Energy Drain) Enemies**
- **Health**: 30 HP
- **Attack**: Drain 10 energy/second in 200px radius
- **Behavior**: Maintain optimal distance
- **Weakness**: Magnetic disruption (polarity switching)

**Green (Agile) Enemies**
- **Health**: 15 HP
- **Movement**: 2× player speed, wall climbing
- **Attack**: Rapid melee strikes (5 damage each)
- **Weakness**: Environmental traps, area denial

**Yellow (Ranged) Enemies**
- **Health**: 25 HP
- **Attack**: Projectiles (10 damage, 400px range)
- **Behavior**: Keep distance, use cover
- **Weakness**: Sonic Wave deflection, magnetic attraction

### Boss Mechanics

**The Scrambler (First Boss)**
- **Phase 1**: Electricity orbs (dodge), floor panels electrify
- **Phase 2**: Magnetic field manipulation, object throwing
- **Vulnerability**: During overload after 3 successful sonic resonances
- **HP**: 150 per phase

**Combat Economy**
- **Player Damage Scaling**: 
  - Basic Sonic: 15 damage
  - Resonant Sonic: 25 damage
  - Environmental: 30-50 damage
- **Enemy Spawn Logic**: 
  - Wave-based spawning with increasing difficulty
  - Maximum 8 enemies active simultaneously

## Progression Systems

### Skill Tree Structure

**Sonic Branch**
- Tier 1: Increased range (+20%)
- Tier 2: Reduced cooldown (0.8s)
- Tier 3: Push function unlock
- Tier 4: Sonic Resonance (combo damage)
- Tier 5: Frequency mastery (wider tolerance)

**Magnetic Branch**
- Tier 1: Increased force (+25%)
- Tier 2: Polarity switching unlock
- Tier 3: Multi-grapple unlock
- Tier 4: Extended duration (+50%)
- Tier 5: Field manipulation (area effects)

**Movement Branch**
- Tier 1: Faster climb speed (+20%)
- Tier 2: Double jump unlock
- Tier 3: Air dash unlock
- Tier 4: Reduced fall speed
- Tier 5: Wall running unlock

### XP & Economy

**XP Sources**
- Puzzle completion: 25-100 XP (based on complexity)
- Enemy defeat: 10-50 XP (based on type)
- Exploration: 5-25 XP (hidden areas)
- Rescue: 150 XP (significant risk/reward)

**Upgrade Costs**
- Tier 1: 100 XP
- Tier 2: 250 XP
- Tier 3: 500 XP
- Tier 4: 750 XP
- Tier 5: 1000 XP

## Procedural Generation System

### Level Chunk Parameters

**Chunk Types**
- **Platforming**: 60% of chunks, focus on movement challenges
- **Puzzle**: 25% of chunks, ability-based challenges
- **Combat**: 15% of chunks, enemy encounters

**Generation Rules**
- Maximum 3 same-type chunks consecutively
- Difficulty gradient: +5% per chunk in sequence
- Theme consistency within zones
- Path validation: Always ensure possible route exists

**Dynamic Elements**
- **Platform Patterns**: 12 predefined movement patterns
- **Enemy Placement**: Distance-based spawning rules
- **Puzzle Variety**: 3-5 variations per puzzle type

## Technical Implementation

### Physics Parameters

**Player Physics**
- Gravity: 1800 px/s²
- Ground acceleration: 3600 px/s²
- Ground deceleration: 4800 px/s²
- Air acceleration: 1800 px/s²

**Object Physics**
- Default friction: 0.92
- Air resistance: 0.98
- Elasticity: 0.3 (most objects), 0.8 (bouncy surfaces)

### Optimization Settings

**Render Layers**
- Background: Parallax (0.5x, 0.7x, 1.0x)
- Main gameplay: 1.0x
- Foreground: 1.0x (non-interactive)
- UI: Fixed position

**Performance**
- Target FPS: 60
- Chunk loading: 2 chunks ahead
- Object pooling: 20 instances per object type
- LOD: Reduced particle effects at distance

## Control Scheme

### Default Bindings
- **Movement**: Arrow Keys / Left Stick
- **Jump**: Z / A Button
- **Sonic Wave**: X / X Button
- **Magnetism**: C / B Button
- **Echolocation**: V / Y Button
- **Polarity Switch**: Left Shift / Left Bumper
- **Interact**: E / Right Bumper

### Input Handling
- Buffer time: 0.1s for all actions
- Simultaneous input: 3-key rollover minimum
- Analog sensitivity: 0.2 deadzone, 0.8 max threshold

## Accessibility Settings

### Visual Options
- **Colorblind Modes**: Protanopia, Deuteranopia, Tritanopia
- **High Contrast**: Enemy outlines, interactive object highlighting
- **UI Scaling**: 100%, 125%, 150%
- **Subtitles**: Background opacity, text size, speaker labels

### Difficulty Options
- **Puzzle Hint Timing**: 30s, 60s, 120s, Never
- **Combat Difficulty**: Reduced enemy damage (50%, 75%, 100%)
- **Platform Assistance**: Extended coyote time, reduced fall speed
- **Auto-Assist**: Optional automated complex sequences

### Control Options
- **Remapping**: Full key/button customization
- **Stick Sensitivity**: 5 adjustment levels
- **Vibration**: Intensity control (0-100%)
- **Button Prompts**: Dynamic switching between keyboard/gamepad

## Version History
- **1.0**: Base movement and ability systems
- **1.1**: Enemy AI and combat implementation
- **1.2**: Puzzle systems and procedural generation
- **1.3**: Progression systems and skill tree
- **1.4**: Polish, optimization, and accessibility

---
*"Great mechanics feel invisible—players should feel powerful, not think about inputs."*
