### # 🚀 NOVA STRIKE — 2D Space Shooter

<div align="center">

<!-- ANIMATED / DYNAMIC LIVE DEMO BUTTONS -->
[![Live Demo](https://img.shields.io/badge/▶__LIVE_DEMO__-__PLAY_NOW__-ff0055?style=for-the-badge&logo=rocket&logoColor=white)](https://livedashboardsite.github.io/space-shooter-2d-game/)
[![GitHub Pages](https://img.shields.io/badge/Deployment-GitHub_Pages-181717?style=for-the-badge&logo=github&logoColor=white)](https://livedashboardsite.github.io/space-shooter-2d-game/)

<br/>

> ⚡ **Built Live During:** Vedam School of Technology × Amazon AI BootCamp 2 (June 28, 2026)  
> 🎓 **Mentored By:** **Tanishq Gupta** (SDE-2, Amazon)

---

### 🚀Live Demo - Live link - https://livedashboardsite.github.io/space-shooter-2d-game/
*(No downloads, no installs. Pure HTML5/JavaScript magic.)*

</div>

---

## 🎮 What Is This?

**Nova Strike** is a fully browser-playable 2D space shooter game built from scratch using HTML, CSS, and JavaScript. 

Developed during a rigorous live 2.5-hour AI BootCamp session, this project demonstrates the power of **"vibe coding"**—breaking complex game mechanics down into micro-components and using AI tools to iterate, debug, and ship production-ready software at lightning speed.

---

## ✨ Features Breakdown

### 🛸 Three Unique Atmospheres
Every single mode shifts the entire aesthetic of the game dynamically.

| Mode | Vehicle | Enemies | Vibe |
|:---:|---|---|---|
| **🌌 Space** | Rocket ship | Alien ships | Deep cosmos, stars, cold neon |
| **🌍 Earth** | Fighter jet | Enemy planes | Sky combat, rushing clouds, tactical |
| **🔮 Fantasy** | Dragon rider | Magical creatures | Mystic realm, glowing orbs, ethereal |

> 🎨 **Atmosphere Isolation:** Each mode has its **own custom visual style, enemy designs, bullet configurations, and dedicated background music.**

### 💀 Smart "Game Over" Matrix
When your ship is taken down (via enemy projectile, direct collision, or an aggressive Boss encounter), a custom menu overlay animates into view with three precise routing paths:

*   **`▶ CONTINUE FROM LEVEL [X]`** — *The Checkpoint System.* Dynamically detects the exact level you died on. Restarts that level with full HP while preserving your score checkpoint.
*   **`⌂ MAIN MENU`** — *The Return.* Safely routes you back to the home screen instantly. Keeps your pilot name cached in the input field for fast re-entry.
*   **`↺ RESTART — START OVER`** — *The Hard Reset.* Wipes the slate completely clean: Level 1, Score 0, fresh seed.

### 📊 Kill-Based Level Progression (20 Levels)
Forget traditional score-grinding. Leveling up requires tactical execution:
*   The **level progress bar fills strictly based on enemy kills**, scaling systematically via the formula:
    $$killsNeeded = 10 + (level \times 4)$$
*   **Level 1** requires **14 kills** $\rightarrow$ **Level 20** requires **90 kills**.
*   Filling the bar fires a flashing, non-blocking **"LEVEL X COMPLETE!"** graphical banner, resets the meter, and advances the game state.
*   Reaching **Level 20** unlocks **Endless Combat Mode** where enemy attributes stay maxed out.

### ⚡ Dynamic Difficulty Scaling (Level 1 $\rightarrow$ 20)
The engine smoothly scales game state variables linearly across 20 levels:

| System Mechanic | Level 1 (Baseline) | Level 20 (Max Chaos) |
|---|---|---|
| **Enemy Speed Multiplier** | $1.0\times$ | $2.8\times$ |
| **Spawn Interval** | ~67 frames | 10 frames *(Hard Minimum)* |
| **Armored Enemy Frequency** | $15\%$ | $50\%+$ |
| **Boss Health Points (HP)** | $23\text{ HP}$ | $175\text{ HP}$ |
| **Boss Fire Rate** | Every 84 frames | Every 10 frames |
| **Boss Spawn Interval** | 40 seconds | ~25 seconds |

### 🎵 Layered Audio System (Zero Overlap Guarantee)
The game runs on a strict audio routing lifecycle utilizing **four native Web Audio API synthesizer tracks**:

*   `menu` 🔊 **Home Screen:** High-energy driving synth — punchy bass, fast arpeggios, chord stabs.
*   `space` 🔊 **Space Gameplay:** Eerie drone — sub-bass, tremolo pulses, slow cosmic arpeggios.
*   `earth` 🔊 **Earth Gameplay:** Aerial combat — punchy bass, fast staccato lead melody.
*   `fantasy` 🔊 **Fantasy Gameplay:** Orchestral — vibrato strings, harp cascades, deep cinematic bass.

> 🔒 **Isolation Guard:** Toggling screens triggers a synchronized `stopBgMusic()` and `startBgMusic()` sequence. Level music cannot blend with menu music, even during rapid UI navigation.

### 💥 Complete Destruction Sequence
When your health pool strikes $0$, the engine pauses standard rendering and triggers a multi-stage cinematic sequence:
1. **Instant Culling:** The player ship sprite vanishes immediately to prevent ghost-frame flickering.
2. **Particle Blast:** Generates a **multi-ring burst explosion** displaying 4 expanding concentric rings alongside 50 physical velocity particles.
3. **Screen Flash:** Flashes the browser viewport white for 1 frame to simulate high-impact feedback.
4. **Retro Sound Synthesis:** Silences all standard gameplay sounds to play an audio rhythm pattern via raw sawtooth oscillators: `ta (pause) ta ta ta ta-ta (pause) taaaa`.
5. **UI Ingress:** After exactly 1.5 seconds, the interactive Game Over pop-up smoothly animates into view.

### ⚡ Drop-System Powerups
Dropped onto the battlefield every 8–12 seconds. Collect them by flying through them:

| Icon | Powerup Type | Technical Performance |
|:---:|---|---|
| **⚡** | **Rapid Fire** | Splits weapon output into triple bullets and doubles fire rate for 5s. |
| **🛡️** | **Shield** | Modifies the player damage mitigation multiplier to $0$ for 5s. |
| **💥** | **Nuke** | Evaluates all active enemy objects on screen and calls their destruction methods instantly. |
| **❄️** | **Freeze** | Drops enemy and boss velocity vectors down to $20\%$ of base speed for 5s. |

### 💬 Combo Matrix & Boss Encounters
*   **Combo Meter:** Chain quick kills to stack multipliers up to $5\times$. High chains render a glowing, responsive **"Nx COMBO!"** UI banner over the canvas.
*   **Boss Ingress:** Bosses spawn systematically every ~40 seconds. Exactly 2 seconds prior to arrival, the engine hands you a **Rapid Fire** buff as a warning. Boss bullet configurations change dramatically by tier:
    *   *Tier 1–2:* Direct targeted spread shots.
    *   *Tier 3:* Radial $360^{\circ}$ bullet rings.
    *   *Tier 4:* Targeted spreads synchronized with a continuous rotating spiral.
    *   *Tier 5+:* Full-grid chaos (Targeted spread + Spiral + Random burst vectors).

---

## 🕹️ Controls

| Action | Primary Key | Secondary Input |
|---|---|---|
| **Movement** | `W` `A` `S` `D` | `↑` `↓` `←` `→` Arrows |
| **Primary Fire** | `Spacebar` | `Left Mouse Click` |
| **Pause Engine** | `P` | — |

---

## 🚀 Installation & Execution

Because the game engine features absolute modular zero-dependency architecture, running it is simple:

1. **Clone or Download** this repository.
2. **Double-click** `index.html` to execute it directly inside any standard browser engine (Google Chrome highly recommended).
3. Input your Pilot Name, choose your atmosphere, and launch.

```yaml
No Build Tools. No Node Modules. No Webpack. No Local Server Required. Pure Vanilla Core. [CLICK HERE TO LAUNCH THE GAME DIRECTLY IN YOUR BROWSER] 🌌
*(No downloads, no installs. Pure HTML5/JavaScript magic.)*

</div>

---

## 🎮 What Is This?

**Nova Strike** is a fully browser-playable 2D space shooter game built from scratch using HTML, CSS, and JavaScript. 

Developed during a rigorous live 2.5-hour AI BootCamp session, this project demonstrates the power of **"vibe coding"**—breaking complex game mechanics down into micro-components and using AI tools to iterate, debug, and ship production-ready software at lightning speed.

---

## ✨ Features Breakdown

### 🛸 Three Unique Atmospheres
Every single mode shifts the entire aesthetic of the game dynamically.

| Mode | Vehicle | Enemies | Vibe |
|:---:|---|---|---|
| **🌌 Space** | Rocket ship | Alien ships | Deep cosmos, stars, cold neon |
| **🌍 Earth** | Fighter jet | Enemy planes | Sky combat, rushing clouds, tactical |
| **🔮 Fantasy** | Dragon rider | Magical creatures | Mystic realm, glowing orbs, ethereal |

> 🎨 **Atmosphere Isolation:** Each mode has its **own custom visual style, enemy designs, bullet configurations, and dedicated background music.**

### 💀 Smart "Game Over" Matrix
When your ship is taken down (via enemy projectile, direct collision, or an aggressive Boss encounter), a custom menu overlay animates into view with three precise routing paths:

*   **`▶ CONTINUE FROM LEVEL [X]`** — *The Checkpoint System.* Dynamically detects the exact level you died on. Restarts that level with full HP while preserving your score checkpoint.
*   **`⌂ MAIN MENU`** — *The Return.* Safely routes you back to the home screen instantly. Keeps your pilot name cached in the input field for fast re-entry.
*   **`↺ RESTART — START OVER`** — *The Hard Reset.* Wipes the slate completely clean: Level 1, Score 0, fresh seed.

### 📊 Kill-Based Level Progression (20 Levels)
Forget traditional score-grinding. Leveling up requires tactical execution:
*   The **level progress bar fills strictly based on enemy kills**, scaling systematically via the formula:
    $$killsNeeded = 10 + (level \times 4)$$
*   **Level 1** requires **14 kills** $\rightarrow$ **Level 20** requires **90 kills**.
*   Filling the bar fires a flashing, non-blocking **"LEVEL X COMPLETE!"** graphical banner, resets the meter, and advances the game state.
*   Reaching **Level 20** unlocks **Endless Combat Mode** where enemy attributes stay maxed out.

### ⚡ Dynamic Difficulty Scaling (Level 1 $\rightarrow$ 20)
The engine smoothly scales game state variables linearly across 20 levels:

| System Mechanic | Level 1 (Baseline) | Level 20 (Max Chaos) |
|---|---|---|
| **Enemy Speed Multiplier** | $1.0\times$ | $2.8\times$ |
| **Spawn Interval** | ~67 frames | 10 frames *(Hard Minimum)* |
| **Armored Enemy Frequency** | $15\%$ | $50\%+$ |
| **Boss Health Points (HP)** | $23\text{ HP}$ | $175\text{ HP}$ |
| **Boss Fire Rate** | Every 84 frames | Every 10 frames |
| **Boss Spawn Interval** | 40 seconds | ~25 seconds |

### 🎵 Layered Audio System (Zero Overlap Guarantee)
The game runs on a strict audio routing lifecycle utilizing **four native Web Audio API synthesizer tracks**:

*   `menu` 🔊 **Home Screen:** High-energy driving synth — punchy bass, fast arpeggios, chord stabs.
*   `space` 🔊 **Space Gameplay:** Eerie drone — sub-bass, tremolo pulses, slow cosmic arpeggios.
*   `earth` 🔊 **Earth Gameplay:** Aerial combat — punchy bass, fast staccato lead melody.
*   `fantasy` 🔊 **Fantasy Gameplay:** Orchestral — vibrato strings, harp cascades, deep cinematic bass.

> 🔒 **Isolation Guard:** Toggling screens triggers a synchronized `stopBgMusic()` and `startBgMusic()` sequence. Level music cannot blend with menu music, even during rapid UI navigation.

### 💥 Complete Destruction Sequence
When your health pool strikes $0$, the engine pauses standard rendering and triggers a multi-stage cinematic sequence:
1. **Instant Culling:** The player ship sprite vanishes immediately to prevent ghost-frame flickering.
2. **Particle Blast:** Generates a **multi-ring burst explosion** displaying 4 expanding concentric rings alongside 50 physical velocity particles.
3. **Screen Flash:** Flashes the browser viewport white for 1 frame to simulate high-impact feedback.
4. **Retro Sound Synthesis:** Silences all standard gameplay sounds to play an audio rhythm pattern via raw sawtooth oscillators: `ta (pause) ta ta ta ta-ta (pause) taaaa`.
5. **UI Ingress:** After exactly 1.5 seconds, the interactive Game Over pop-up smoothly animates into view.

### ⚡ Drop-System Powerups
Dropped onto the battlefield every 8–12 seconds. Collect them by flying through them:

| Icon | Powerup Type | Technical Performance |
|:---:|---|---|
| **⚡** | **Rapid Fire** | Splits weapon output into triple bullets and doubles fire rate for 5s. |
| **🛡️** | **Shield** | Modifies the player damage mitigation multiplier to $0$ for 5s. |
| **💥** | **Nuke** | Evaluates all active enemy objects on screen and calls their destruction methods instantly. |
| **❄️** | **Freeze** | Drops enemy and boss velocity vectors down to $20\%$ of base speed for 5s. |

### 💬 Combo Matrix & Boss Encounters
*   **Combo Meter:** Chain quick kills to stack multipliers up to $5\times$. High chains render a glowing, responsive **"Nx COMBO!"** UI banner over the canvas.
*   **Boss Ingress:** Bosses spawn systematically every ~40 seconds. Exactly 2 seconds prior to arrival, the engine hands you a **Rapid Fire** buff as a warning. Boss bullet configurations change dramatically by tier:
    *   *Tier 1–2:* Direct targeted spread shots.
    *   *Tier 3:* Radial $360^{\circ}$ bullet rings.
    *   *Tier 4:* Targeted spreads synchronized with a continuous rotating spiral.
    *   *Tier 5+:* Full-grid chaos (Targeted spread + Spiral + Random burst vectors).

---

## 🕹️ Controls

| Action | Primary Key | Secondary Input |
|---|---|---|
| **Movement** | `W` `A` `S` `D` | `↑` `↓` `←` `→` Arrows |
| **Primary Fire** | `Spacebar` | `Left Mouse Click` |
| **Pause Engine** | `P` | — |

---

## 🚀 Installation & Execution

Because the game engine features absolute modular zero-dependency architecture, running it is simple:

1. **Clone or Download** this repository.
2. **Double-click** `index.html` to execute it directly inside any standard browser engine (Google Chrome highly recommended).
3. Input your Pilot Name, choose your atmosphere, and launch.

```yaml
No Build Tools. No Node Modules. No Webpack. No Local Server Required. Pure Vanilla Core.
