# LuminaSwarm (Group 2) - Assignment 5 Beta Build

**Group Members:** Bryan Shangguan (netID: bys8), Yijia Zhang (netID: yz1975)  
**Live WebGL Build:** [https://yz1975-creator.github.io/cs425/](https://yz1975-creator.github.io/cs425/)  
**Source Code:** [https://github.com/yz1975-creator/cs425](https://github.com/yz1975-creator/cs425)

## Quick Review of Primary Pillar: Swarm and Boids Modeling

- **Description:** Our first pillar focused on a high-performance boids simulation using a Spatial Hash Grid and Structure of Arrays (SoA) to handle thousands of agents.
- **Achievements:** We successfully implemented core kinematics for Separation, Alignment, and Cohesion, allowing the swarm to navigate toward energy sources with fluid, organic movement.

## Secondary Pillar Integration: Advanced VFX & Behavior Trees

- **Integration:** The secondary technical pillar—NPC AI (Behavior Trees) and Advanced GLSL Shaders—is now fully integrated into the core software loop.
- **Core Loop Connection:** The Behavior Tree manages the state transition between "Seeker" (hungry) and "Wanderer" (fed) agents based on their proximity to the player-controlled Energy Source.
- **Interactive Feedback:** These AI states are directly linked to the GPU buffers; as agents are "fed," the `CustomVFXShader` and `UnrealBloomPass` dynamically increase the "overcharge" factor, shifting the scene's fog, grid colors, and bloom intensity to signal progress toward the win condition.

## New Features (Since Alpha Build)

- **Custom VFX Pipeline:** Implemented a `ShaderPass` with radial blur and chromatic aberration that scales based on the Energy Source’s velocity.
- **Interactive Energy Source:** Added WASD controls to allow the user to manually navigate the Energy Source, transforming the project from a simulation into an interactive game.
- **Dynamic Fog & Lighting:** Integrated a reactive environment where the `FogExp2` density and background colors shift from deep blue to vibrant pink as the swarm reaches 90% saturation.
- **Game State Management:** Added a complete UI/UX loop including a start menu, a real-time system HUD, and win/loss end screens.

## Changes Since Alpha Build (Assignment 4)

- **Visual Cohesion:** Moved away from "programmer art" by implementing a unified neon-cyberpunk aesthetic with coordinated post-processing.
- **Stability Improvements:** Refined the agent update logic to include a `repairParticle` function, preventing simulation crashes if entity coordinates become non-finite.
- **Performance Optimization:** Adjusted the active agent count to 2,000 units to ensure a stable 60 FPS target while running the new complex shader passes and bloom effects.

## Known Issues

- **Post-Processing Load:** On lower-end integrated GPUs, the combination of `UnrealBloomPass` and the `CustomVFXShader` may cause the frame rate to dip below the target when the "overcharge" effect is at maximum.
- **Boundaries:** The Energy Source can currently be moved slightly beyond the visible grid helper if the player holds a movement key for an extended period.
- **Mobile UI:** The HUD text is optimized for desktop and may overlap on mobile screens with aspect ratios narrower than 16:9.
