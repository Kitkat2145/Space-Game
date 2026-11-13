# Space Bar

Chapter 1: Race to the Moon. A browser game for NASA Space Apps Challenge, Port Louis, Mauritius.

You run a 1960s Moon program. You make three decisions, build the rocket on the pad part by part, and fly the mission yourself.

Built with TypeScript, Vite and three.js.

## Run it

You need [Node.js](https://nodejs.org) 20 or newer.

```bash
npm install
npm run dev
```

Then open http://localhost:5173.

## Other commands

- `npm run build` checks the types and builds a static site into `dist/`. You can host that folder on GitHub Pages, Netlify or itch.io.
- `npm test` runs the simulation, flying and session tests.
- `npm run e2e` plays the whole game in Chrome, by autopilot and by a scripted pilot. Start `npm run dev` first.

## How to play

- **Decide.** Three story decisions: funding, the schedule, and what to do after a cabin fire. Hold a choice to commit to it.
- **Build.** Six spots on the rocket: lander, docking, power, antenna, science and the spent stage. Click a spot, then a part. Swap freely until you roll out. A lighter ship has more landing fuel.
- **Fly.** Three controls, the same in every moment: turn with ← → (or A D), hold the space bar for the engine, set the throttle with ↑ ↓ (or W S). On-screen buttons do the same for a mouse or a finger. Each moment starts with a short "how to" card, and a coach at the side lights the step you are on.
  - Liftoff: hold the engine, turn to stay on the guide arrow as it leans over, and when the first stage runs dry let go and press again to light the next.
  - Moon orbit: turn the ship around to the arrow, hold the engine, and let go when the speed is inside the green band.
  - Landing: cancel your sideways speed, turn upright, brake before the ground. The numbers beside the lander turn green when they are safe. A bad first try aborts back up for one more.
- Let go of the turn keys near the guide arrow and the craft settles onto it.
- Each flying moment has a "Let the autopilot fly" link.

## URL options

- `?intro=1` always plays the intro.
- `?seed=21` gives a repeatable run.
- `?quick=1` lets you lock in a choice with a single click instead of holding it, and hands the flying to the autopilot.
- `?fly=1` with `?quick=1` keeps the flying in your hands.
- `?fast` speeds up the launch, for testing.
- `?practice=liftoff`, `?practice=orbit` and `?practice=landing` go straight to that moment and back to it every time, for learning the controls. Nothing is saved.

## Where things are

- `src/main.ts`: the screens and game flow.
- `src/data/`: the story, the questions, events, endings and the chapter settings.
- `src/sim/`: the simulation that decides whether the mission works. `ascent.ts`, `orbit.ts` and `landing.ts` hold every rule and number for the flying.
- `src/three/`: the 3D launch pad, rocket and spacecraft, `flight.ts` (the flight you fly) and `landerview.ts` (the side view of the landing).
- `src/ui/`: meters, sound, the flying controls (`flycontrols.ts`) and the flying overlays (`flyhud.ts`).
- `public/textures/`: drop real NASA imagery here, credited to NASA.
