Čeka dok se učitaju slike da bi počeo game loop:

```js
Game.assetLoadingLoop = function () {
  if (Game.spritesStillLoading > 0)
    window.requestAnimationFrame(Game.assetLoadingLoop);
  else {
    Game.initialize();
    Game.mainLoop();
  }
};
```
