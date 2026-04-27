# Assignment 6 – Feature Complete Report

# LuminaSwarm v1.0

## 1. Overview

LuminaSwarm is a 3D swarm simulation made with JavaScript and Three.js.

In this version, the player controls an energy source with WASD. The swarm reacts to the source. Hungry agents move toward it, and fed agents start moving away and wandering again.

The goal is to keep 90% of the agents fed for 5 seconds before the 60 second timer runs out.

This is our feature complete build. The main game loop, UI, audio, visuals, swarm behavior, win condition, loss condition, and restart flow are all working. After this point, we are not planning to add new major features. The rest of the work will be balancing, bug fixing, and polish.

---

## 2. Feature Complete Release Notes

Since the beta build, we finished the remaining systems needed for the full version of the project.

### Game Flow

The game now has a complete flow from start to finish:

- main menu
- play state
- win screen
- loss screen
- restart back to menu

The player can start the simulation, play one full round, either win or lose, and then return to the menu.

### Final Objective

The final objective is now implemented.

The player has 60 seconds to feed the swarm. To win, at least 90% of the agents must stay fed for 5 seconds. If the timer reaches zero first, the player loses.

This makes the project feel more like a playable game instead of only a visual simulation.

### Swarm and Agent Behavior

The swarm uses boids-style movement, including separation, alignment, and cohesion.

Agents also react differently depending on their energy state:

- hungry agents move toward the energy source
- fed agents move away from the source
- agents still stay connected to the swarm through boids movement

This is the main AI behavior of the project.

### Energy Source

The player-controlled energy source is now fully working.

It can be moved with WASD. It has a visible core, glow, and ring. It also has boundary limits, so the player cannot move it outside the simulation area.

Agents gain energy when they are close enough to the source and slowly lose energy when they are outside the range.

### UI and Instructions

The main menu now explains the controls and goal before the player starts.

The HUD shows:

- agent count
- time left
- timer bar
- fed swarm percentage
- progress toward the 5 second win condition

There is also a quality selector for high and low modes.

### Visual Effects

The final build includes the main visual style we wanted:

- glowing swarm trails
- bloom effect in high quality mode
- fog
- animated source glow
- rotating energy ring
- color changes when the swarm gets close to winning
- grid floor for orientation

These effects make the simulation look more complete and easier to read.

### Audio

Audio was added for feedback and atmosphere.

The build includes:

- ambient background sound
- energy source hum
- feeding sound
- win sound
- loss sound

The source hum changes based on swarm progress, so the sound gives feedback while playing.

### Performance and Stability

We added a low quality mode with fewer agents for smoother performance.

The code also includes a spatial grid for nearby agent checks, particle repair for invalid positions, and delta time limiting to avoid large simulation jumps.

These changes helped make the build more stable for playtesting.

### Production Plan Status

The main features from our production plan are now included:

- swarm AI
- player-controlled energy source
- energy and feeding system
- visual effects
- audio feedback
- HUD and menu
- win/loss game loop
- quality setting

No major planned feature was cut in this sprint. From now on, the focus will be polish and optimization instead of adding new systems.

---

## 3. Playtesting Method

We asked 5 classmates outside of our group to play the feature complete build.

Before they started, we only explained the basic idea of the project. We did not explain the controls directly because we wanted to see if the menu instructions were clear enough.

While they played, we watched how they moved, whether they understood the goal, where they got confused, and whether the game had lag or visual problems.

After each test, we asked:

- What was confusing?
- How did the controls feel from 1 to 10?
- Did you notice lag, bugs, or visual glitches?

---

## 4. Playtesting Results

### Subject 1

Subject 1 learned WASD movement quickly and said the controls were easy to understand.

At first, they were not sure if they should chase the swarm or wait for the swarm to come to them. After playing for a short time, they understood that they needed to move the source toward the swarm.

They did not win. They said the fed agents moved away too fast.

Controls: 8/10

---

### Subject 2

Subject 2 liked the glow and particle effects.

They understood the timer, but the “90% for 5 seconds” rule was not clear immediately. They had to read the instructions again.

They also said the fed percentage dropped too quickly, even when they stayed near the swarm.

Controls: 7/10

---

### Subject 3

Subject 3 noticed lag in high quality mode when many agents were close together.

After switching to low quality mode, the game felt smoother. This showed that the quality option helped, but high quality mode still needs optimization.

They understood the goal but still could not reach 90%.

Controls: 8/10

---

### Subject 4

Subject 4 liked the audio feedback and said it made the game feel more responsive.

They understood the goal from the menu and got close to winning. However, they lost near the end because keeping the percentage above 90% for 5 seconds was difficult.

Controls: 9/10

---

### Subject 5

Subject 5 said the game looked complete and liked the energy source visuals.

They were confused about the exact range of the energy source. They did not know how close agents needed to be to recharge.

They also said fed agents seemed to move away too quickly.

Controls: 8/10

---

## 5. Feedback Summary

Overall, players understood the basic controls and the main idea of the game.

The parts that worked well were:

- the glowing visual style
- the swarm movement
- the audio feedback
- the main menu instructions
- the high and low quality options

The biggest issue was difficulty. None of the testers won with the current settings. Most of them said the fed percentage dropped too quickly or the agents moved away too fast.

One tester changed a few values in the code, including reducing how strongly fed agents move away and slowing down energy loss. After that, they were able to win. This suggests that the game systems work, but the current balance is too harsh.

---

## 6. Action Items for Assignment 7

For the next sprint, we plan to:

1. Reduce how fast fed agents move away from the source.
2. Slow down energy loss.
3. Make the source range easier to see.
4. Improve performance in high quality mode.
5. Reduce repeated feeding sounds.

---

## 7. Build and Code

Live Build:

https://yz1975-creator.github.io/cs425/

GitHub:

https://github.com/yz1975-creator/cs425/

Run Instructions:

The project uses vanilla JavaScript, ES6 modules, and Three.js from a CDN. It does not need Node.js or a build tool.

To run locally:

1. Download or clone the repository.
2. Open `index.html` in a modern browser.
3. Keep an internet connection so Three.js can load from the CDN.

Controls:

- WASD: move the energy source
- Mouse drag: rotate the camera
- Scroll wheel: zoom

---

## 8. Conclusion

LuminaSwarm is now feature complete.

The game can be played from start to finish. The swarm behavior, energy source, UI, visual effects, audio, timer, win condition, loss condition, and restart flow are all working.

The playtest showed that the main problem is balance. The project does not need new features right now. For Assignment 7, we will focus on making the game easier to understand, smoother to run, and fairer to win.
