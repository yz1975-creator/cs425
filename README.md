cs425
luminaswarm
midterm report

Project Links:
- Repo: [Insert Link]
- WebGL Build: [Insert Link]
- Video: [Insert Link]

PLAN VS REALITY

Features from Assignment 2 MVP implemented:
- 3D Boids algorithm (Separation, Alignment, Cohesion) is functional.
- Behavior Tree is implemented. Agents transition between Seek (hungry) and Wander (full) states based on distance to the center.
- GLSL shaders for energy visualization are working. High-level logic passes data via Float32Arrays to the GPU to change agent colors.
- We scaled the simulation to 12,000 agents at 60fps using a Spatial Hash Grid and Structure of Arrays (SoA).

Features cut or changed:
- Cut: Dynamic vector field environment.
- Reason: Combining external vector field forces with Boids separation/cohesion caused "potential well deadlocks." Agents got stuck in static rings and stopped moving. We changed it to a single static energy source to ensure the swarm keeps flying.

USE OF AI

Usefulness of AI tools:
- Helpful: Used LLM to generate Three.js boilerplate code, SoA memory layouts, and basic GLSL syntax. It saved time on API lookups.
- Unhelpful: AI was bad at debugging physics math. When we had the deadlock issue, AI generated flawed formulas that made particles freeze. We had to manually debug the cross-product math and adjust the Boids weights ourselves, which took much longer than expected.

MAP TO FINAL

Remaining tasks for final submission:
- Implement multiple Energy Sources and Sinks instead of just one.
- Add GUI controls for users to dynamically adjust flocking weights and gravity.
- Add WebGL post-processing (e.g., trail persistence and bloom effects).
