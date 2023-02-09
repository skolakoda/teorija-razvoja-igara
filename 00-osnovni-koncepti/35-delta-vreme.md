# Delta vreme

Delta vreme (elapsed time or *delta time*, skraćeno *dt*) je vreme trajanja prethodnog kadra. Zavisi od brzine računara i količine računanja u tom trenutku. Obzirom da trajanje kadrova varira, animacija je brža kad su kadrovi kraći, a sporija kad su kadrovi duži.

Delta vreme se koristi kao korektor da bi animacija bila nezavisna od učestalosti kadrova (*frame rate*):

```js
const speed = 8

update ()
{
    mesh.position += new Vector3(speed * deltaTime, 0, 0);
}
```

## Fiksiran vremenski razmak (*fixed timestep*)

We need a way to ensure that our physics engine only runs when a specific amount of time has passed. This way, the `dt` that is used within calculations is always the exact same number. Using the exact same `dt` value everywhere will actually make your physics engine deterministic, and is known as a fixed timestep. This is a good thing.

A deterministic physics engine is one that will always do the exact same thing every time it is run assuming the same inputs are given.

This waits around, rendering the game, until enough time has elapsed to update the physics:

```js
const fps = 60
const dt = 1 / fps
let accumulator = 0
let frameStart = getCurrentTime() // in seconds

mainLoop() {
  const currentTime = getCurrentTime()
  // store the time elapsed since the last frame began
  accumulator += currentTime - frameStart()
  // record the starting of this frame
  frameStart = currentTime

  while(accumulator > dt) {
    updatePhysics(dt)
    accumulator -= dt
    renderGame()      
  }
}
```

There are a couple of problems that can be fixed here. The first involves how long it takes to actually perform the physics update: What if the physics update takes too long and the accumulator goes higher and higher each game loop? This is called the *spiral of death*.

To solve this, the engine really needs to just run fewer physics updates if the accumulator gets too high. A simple way to do this would be to clamp the accumulator below some arbitrary value.

Pre while petlje dodajemo ovaj red, da bismo izbegli spiralu smrti and clamp `dt`, thus clamping how many times the `updatePhysics` can be called in a single game loop:

```js
if (accumulator > 0.2) accumulator = 0.2
```
