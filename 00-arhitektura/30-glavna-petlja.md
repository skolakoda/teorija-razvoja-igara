# Glavna petlja (*Main loop*)

Here's an example of a game loop:
```js
function mainLoop() {
  handleInput()
  update()
  render()
}
```

It is important that draw() is called after update() because we want the screen to reflect a state of the application.

A typical main loop may receive and process player input, run creature AI, update animations, update the physics system, run any world simulation that needs to happen, render the scene, and play music and sound effects. Every main loop is different and tailored for each individual game.

In pseudocode, might look something like this:

```
while( user doesn't exit )
  check for user input
  run AI
  move enemies
  resolve collisions
  draw graphics
  play sounds
end while
```

Malo detaljniji loop može biti podeljen na update i render. Update loop može izgledati ovako:
```
Player update
   Sense Player input
   Compute restrictions
   Update player state
World update
   Passive elements
      Pre-select active zone for engine use
   Logic-based elements
      Sort according to relevance
      Execute control mechanism
      Update state
   AI based elements
      Sort according to relevance
      Sense internal state and goals
      Sense restrictions
      Decision engine
      Update world
End
```

Render loop može izgledati ovako:
```
World presentation
   Select visible subset (graphics)
      Clip
      Cull
      Occlude
   Select resolution
   Pack geometry
   Render world geometry
   Select audible sound sources (sound)
      Pack audio data
      Send to audio hardware
NPC presentation
   Select visible subset
   Animate
   Pack
   Render NPC data
Player presentation
   Animate
   Pack
   Render
```

All of these operations occur in one giant loop that can’t take longer than 33ms per iteration (30 iterations per second).

Za razliku od klasičnih programa, even if the player does absolutely nothing, the game still needs to be constantly thinking and processing.

![game-loop](slike/game-loop.png)

One problem with rendering is that your CPU spends most of its time waiting for the video card to process what it just sent. By putting the rendering system on another thread, you free up the CPU while the GPU is working its magic.

![multithread-game-loop](slike/multithread-game-loop.png)

# Glavna petlja sa delta vremenom

```js
var then = Date.now();

var main = function () {
	var now = Date.now();
	var delta = now - then;
	update(delta / 1000);
	render();
	then = now;
	requestAnimationFrame(main);
}
```

We get the modifier to send to update by dividing by 1000 (the number of milliseconds in one second).

```js
var update = function (modifier) {
	hero.x -= hero.speed * modifier;
}
```

Modifier is a time-based number based on 1. If exactly one second has passed, the value will be 1 and the hero's speed will be multiplied by 1. If one half of a second has passed, the value will be 0.5 and the hero will have moved half of his speed, and so forth. This function gets called so rapidly that the modifier value will typically be very low, but using this pattern will ensure that the hero will move the same speed no matter how fast the script is running.

# Merenje brzine

You typically aim for a target of 30-60 frames per second, which means game loop must fit within 33-16 milliseconds.

![](slike/petlja.gif)

![](slike/potrosnja.gif)
