# LuminaSwarm (Group 2) - Assignment 7 Final Submission & Post-Mortem

## Group Members

- Bryan Shangguan (netID: bys8)
- Yijia Zhang (netID: yz1975)

## Project Title

**LuminaSwarm - Large-scale Agent Simulation**

## Final Build / Web Link

https://yz1975-creator.github.io/cs425/

## Source Code

https://github.com/yz1975-creator/cs425

## Final Demo Video

https://youtu.be/fu9w-eXCU4o?si=Lb9gfWsdEmvB_Mq3

---

## 1. Brief Overview

LuminaSwarm is a real-time WebGL large-scale agent simulation built with vanilla JavaScript, ES6 Modules, and Three.js. The project started as a technical swarm demonstration and gradually became a complete interactive software experience. By the Alpha stage, the project already included a complete software loop, real-time monitoring UI, and interaction logic based on user input.

The final version continues from the Alpha build and focuses on polish, optimization, stability, and final presentation. Instead of adding new mechanics during the final buffer phase, we focused on improving the existing system and making the final build more reliable.

The main experience is built around a complete loop:

**Start Menu → Active Simulation State → End State**

During the active state, the user can control the energy source using WASD keys. The swarm reacts to the energy source in real time, while the HUD displays status distribution and objective progress for the 12,000 agents.

Our two main technical pillars are:

1. **Swarm and Boids Modeling**
    - The project simulates 12,000 agents in real time.
    - Agent movement is based on swarm behavior and Boids-style rules.
    - The system uses spatial hashing to make large-scale movement more efficient.

2. **NPC AI / Behavior States**
    - Agents respond to the energy source and switch behavior based on their state.
    - The simulation includes state-driven logic instead of purely random movement.
    - Agent states are connected to visual feedback so users can understand the swarm behavior more clearly.

The final build is not only a visual particle demo. It is an interactive simulation with user input, agent behavior, real-time feedback, and a complete software loop.

---

## 2. Build and Run Instructions

This project is built using vanilla JavaScript and Three.js through CDN. It does not require Node.js, Webpack, or any local build tools.

### Option 1: Live WebGL Build

The live project can be opened directly in a modern browser:

https://yz1975-creator.github.io/cs425/

### Option 2: Run Locally

1. Clone or download the repository as a ZIP file.
2. Extract the files to a local machine.
3. Open `index.html` in a modern browser such as Chrome, Edge, or Safari.
4. An active internet connection is required because Three.js is fetched from the CDN.

### Controls

- WASD: move the energy source
- Left click and drag: rotate the camera
- Scroll wheel: zoom in and out
- Right click and drag: pan the camera

---

## 3. Final Achievements

By the final submission, LuminaSwarm includes:

- A complete Start Menu, Active State, and End State.
- A real-time interactive swarm simulation.
- 12,000 simulated agents.
- WASD control of the energy source.
- Real-time HUD showing agent status distribution and objective progress.
- Swarm movement influenced by the energy source.
- Spatial hashing optimization for large-scale agent updates.
- Shader-based visual feedback.
- Color and visual effects connected to agent states.
- Improved browser stability.
- Fixed Delta Time overflow after browser tab switching.
- Fixed input conflicts between menu UI and background canvas interaction.
- Improved HUD readability.
- Improved final presentation and documentation.
- A final hosted WebGL build.
- A final demo video showing the complete game loop and technical pillars.

Compared with the earlier MVP and Alpha builds, the final version is more complete and more stable. The project is no longer only a technical demonstration. It now functions as a complete interactive simulation with a clear user loop, readable feedback, and improved technical reliability.

---

## 4. Playtest Resolution

During Assignment 6, playtesting helped us identify several issues related to clarity, stability, UI, interaction, and performance. In Assignment 7, we used the buffer phase to fix these problems and polish the final build.

No new mechanics were added during this phase. The focus was on improving the existing system, fixing problems, optimizing performance, and making the final experience more complete.

### Issue 1: The objective and game loop were not clear enough

In the earlier build, users could see the swarm simulation running, but the overall software loop was not clear enough. Some users were not sure how the Start Menu, Active State, and End State connected together.

**Fix:**

This issue was fixed by polishing the full software loop. The final build now presents a clearer transition from the Start Menu to the Active Simulation State and then to the End State. The user can better understand when the simulation begins, what happens during the active state, and when the result screen appears.

This makes the project feel more like a complete interactive product instead of only a running simulation.

---

### Issue 2: The HUD was difficult to read during the simulation

The earlier HUD displayed useful information, including agent status distribution and objective progress, but the layout and readability still needed improvement.

**Fix:**

This issue was fixed by refining the HUD layout and improving the clarity of the displayed information. The final HUD is easier to read while the simulation is running and better supports the user’s understanding of the swarm state and progress.

This was important because the project simulates 12,000 agents. Without a readable HUD, users may not understand what is happening at the system level.

---

### Issue 3: Energy source interaction was not clear enough

In the earlier build, the user could control the energy source with WASD, but the connection between user input and swarm behavior was not always visually clear.

**Fix:**

This issue was fixed by polishing the energy source interaction and making the swarm response more readable. In the final build, moving the energy source has a clearer effect on the swarm, so users can better understand how their input influences the agents.

This improves the feeling that the user is actively affecting the simulation instead of simply watching particles move.

---

### Issue 4: Performance needed to be more stable with 12,000 agents

The project’s large-scale simulation created performance pressure, especially when many agents were updating at the same time.

**Fix:**

This issue was improved through optimization work during the final phase. We refined the spatial hashing system, reduced unnecessary per-frame calculations, and tested the project with the full 12,000-agent simulation.

The final build is more stable and reliable during normal interaction.

---

### Issue 5: Menu and canvas input events conflicted

In an earlier version, menu button clicks could conflict with background canvas interaction. This made the interface feel less polished.

**Fix:**

This issue was fixed by adjusting the event handling between the DOM UI and the WebGL canvas. The final build now handles menu interaction and simulation interaction more consistently, making the transition from menu to simulation smoother.

This makes the start menu and active simulation feel more connected and less buggy.

---

### Issue 6: Delta Time overflow after switching browser tabs

An earlier bug occurred when the browser tab was switched away and then returned to the simulation. The time gap could create an abnormally large Delta Time value, which affected the simulation update.

**Fix:**

This issue was fixed by handling abnormal frame time changes more safely. The simulation now avoids large Delta Time spikes after tab switching, which makes the final build more stable.

This fix was important because browser-based projects can easily be affected by tab switching, frame pauses, and inconsistent timing.

---

## 5. Technical Post-Mortem

### Biggest Engineering Challenges

The biggest engineering challenge was scaling the simulation to 12,000 agents while keeping the browser experience interactive. At this scale, simple brute-force logic becomes too expensive. Every unnecessary calculation inside the frame loop can affect performance.

Spatial hashing became one of the most important parts of the project. It helped reduce the cost of checking nearby agents and made the swarm simulation more scalable. However, this also introduced new complexity because the system needed to update agent positions, spatial cells, and behavior states in real time.

Another major challenge was browser stability. Since the project runs in WebGL through a normal browser, we had to account for browser-specific behavior, including frame rate fluctuation and tab switching. One issue we fixed was a Delta Time overflow problem caused by switching browser tabs.

A third challenge was integrating UI with simulation controls. The project includes both DOM-based UI elements and a WebGL canvas. This created input conflicts between menu buttons and canvas interaction, which had to be fixed so the final build felt polished.

The final challenge was communication. A large swarm can look interesting, but users need to understand what is happening. The HUD, visual state feedback, and demo video became important tools for explaining the simulation clearly.

---

## 6. Architecture and System Design

The final project is built around a real-time update loop.

The main systems include:

- Start Menu state
- Active Simulation state
- End State
- 12,000-agent swarm update system
- Spatial hashing system
- Energy source control system
- WASD input handling
- Agent behavior state logic
- Real-time HUD
- Shader-based rendering
- Camera controls
- Browser event handling

The simulation updates agent behavior based on the energy source and the current system state. The user moves the energy source with WASD, and the swarm responds dynamically.

The project’s architecture separates the main concerns:

- The **state system** controls whether the user is in the menu, active simulation, or end screen.
- The **input system** handles WASD movement and camera controls.
- The **swarm system** updates agent positions and behavior.
- The **spatial hashing system** improves performance for large-scale simulation.
- The **HUD system** displays real-time agent information and progress.
- The **rendering system** visualizes the swarm and behavior states.

This separation made the final polish phase easier because we could fix UI, simulation, and performance issues without rewriting the entire project.

---

## 7. Swarm and Behavior Implementation

The swarm system is based on large-scale agent movement. Each agent has position and movement information that updates every frame. The goal is to create a group behavior that feels alive and responsive instead of random.

The project uses Boids-style logic, including:

- **Separation:** agents avoid crowding too closely together.
- **Alignment:** agents tend to move in similar directions.
- **Cohesion:** agents are influenced by nearby group movement and clustering.

On top of the movement logic, the project includes behavior-state logic. Agents respond to their relationship with the energy source. This allows the system to represent different behavior modes rather than treating every agent the same at all times.

The energy source gives the simulation a clear interactive focus. By moving the source with WASD, the user can influence the swarm and observe how the agents respond in real time.

---

## 8. Optimization Work

Optimization was one of the main focuses of the final phase.

The most important optimization work included:

- Improving spatial hashing calculations.
- Reducing unnecessary per-frame updates.
- Stabilizing the simulation under normal browser frame rates.
- Fixing Delta Time overflow after browser tab switching.
- Testing performance with 12,000 agents.
- Keeping shader and rendering work efficient.
- Making the live WebGL build stable enough for final submission.

One known technical limitation from the Alpha stage was that large-scale spatial hashing could still create pressure on low-frequency CPU devices. In the final version, we focused on reducing this issue as much as possible while preserving the project’s large-scale swarm goal.

The final build performs better and feels more stable than earlier versions.

---

## 9. Visual and Aesthetic Polish

The visual goal of LuminaSwarm is to make the swarm feel alive, responsive, and readable.

During the final phase, we polished:

- Agent color feedback.
- Energy source visibility.
- HUD layout and clarity.
- Shader-based visual effects.
- Camera viewing experience.
- Overall presentation for the final demo video.

One earlier known issue was that particle depth sorting could look unnatural during extremely high-density aggregation. This is still a difficult WebGL rendering problem, but we improved the overall readability of the simulation so the visual result remains clear during normal use.

The final aesthetic focuses on showing both scale and behavior. The viewer should be able to see not only that there are many agents, but also that the agents are responding to the energy source and changing state over time.

---

## 10. Pivots and Cut Features

During the Alpha planning stage, we considered procedural audio as a possible secondary feature. However, during the final development phase, we prioritized stability, optimization, HUD clarity, and the core swarm interaction.

We did not add new mechanics during the final buffer phase. This was intentional because the final phase was focused on polish, bug fixing, optimization, and playtest feedback resolution.

Some features were simplified or not expanded further, including:

- More complex procedural audio.
- Additional environmental effects.
- More agent types.
- More complicated game mechanics.

These features could have made the project larger, but they also would have increased the risk of bugs and performance problems. We decided that the best final version would be a more polished and stable version of the existing swarm simulation.

This was the right decision because the core value of LuminaSwarm is the large-scale swarm system, the energy source interaction, and the real-time visualization of agent behavior.

---

## 11. AI Tool Evaluation

We used AI tools as support during the semester, mainly for understanding concepts, debugging smaller issues, organizing ideas, and writing documentation.

AI was useful for:

- Explaining Three.js and WebGL concepts.
- Helping organize technical writing.
- Suggesting possible debugging directions.
- Explaining swarm and behavior-state concepts.
- Helping turn implementation details into clearer report language.

However, AI was not always reliable for direct implementation. Some suggestions did not match our exact code structure or made assumptions that were not true for our project. This was especially true for browser rendering, shader-related behavior, and performance optimization.

AI was less useful for:

- Project-specific WebGL bugs.
- Exact shader and buffer behavior.
- Performance issues that required real testing.
- Input conflicts between UI and canvas.
- Bugs caused by timing or browser behavior.

Overall, AI helped with explanation and planning, but the important engineering work still required manual implementation, testing, debugging, and verification. It was a helpful support tool, not a replacement for development.

---

## 12. What We Learned

This project helped us understand the difference between a technical demo and a complete interactive system.

The main lessons were:

- Large-scale real-time simulations require optimization early.
- Spatial hashing is important when working with many agents.
- Browser-based WebGL projects need careful handling of frame timing.
- UI and canvas input can conflict if events are not managed carefully.
- A HUD can make a complex simulation much easier to understand.
- A complete software loop makes a project feel much more finished.
- Final polish is not just visual; it includes stability, usability, and clarity.

We also learned that technical complexity needs to be communicated clearly. The final demo video and report are important because they explain what the viewer is seeing and why the system is technically meaningful.

---

## 13. Conclusion

LuminaSwarm reached the final release stage as a polished large-scale WebGL agent simulation. The project includes a complete software loop, real-time HUD, WASD-controlled energy source interaction, 12,000-agent swarm behavior, spatial hashing optimization, and shader-based visual feedback.

The final phase focused on making the project more stable, readable, and presentable. Instead of adding new features, we improved the systems that already existed: simulation performance, input reliability, UI clarity, visual feedback, and final documentation.

The final result is a stronger version of the Alpha build and better represents the project’s main technical goals: large-scale swarm modeling and interactive AI-driven behavior.# Welcome to Dillinger

A clean, distraction-free markdown editor. Type on the left, see the rendered output on the right.
