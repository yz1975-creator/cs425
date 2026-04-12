LuminaSwarm (Group 2) - Assignment 5 Beta Build

Group Members: Bryan Shangguan (netID: bys8), Yijia Zhang (netID: yz1975)

Overview
This is the Assignment 3 MVP build for LuminaSwarm. It implements a state-driven swarm simulation navigating towards a static energy source. The project demonstrates our core pillars: Swarm and Boids Modeling, and NPC AI / Behavior Trees.

Build and Run Instructions
This project is built using vanilla JavaScript (ES6 Modules) and Three.js via CDN. It does not require Node.js, Webpack, or any local build tools.

Option 1: Live WebGL Build
You can view the live simulation directly in your browser here:
(https://yz1975-creator.github.io/cs425/)

Option 2: Run Locally
Clone or download this repository as a ZIP file. Extract the files to your local machine. Simply double-click index.html to open it in any modern web browser (Chrome, Edge, Safari). Note that an active internet connection is required to fetch the Three.js library from the unpkg CDN.

Controls
Left Click and Drag to rotate the camera.
Scroll Wheel to zoom in and out.
Right Click and Drag to pan the camera.

Features Implemented
12,000 Agents: Scaled well beyond the 2,000 target using a Spatial Hash Grid and Structure of Arrays.
Boids Algorithm: Custom kinematics for Separation, Alignment, and Cohesion.
Behavior Tree: Agents dynamically switch between Seeker and Wanderer states based on their distance to the energy source.
GLSL Shaders: High-level behavior states are linked to GPU buffers to drive real-time velocity alignment and color rendering (Cyan for Seekers, Magenta for Wanderers).
