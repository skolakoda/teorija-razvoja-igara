# Upravljanje unosima (*Input Manager class*)

The first important difference from web development is that the input events doesn't actually do anything right away. If a user presses a key in a typical web app, it makes sense to immediately perform the desired action. But in a game, things have to happen in chronological order to flow correctly.

Često se inputi obrađuju na početku game loop-a:
```js
function mainLoop() {
  handleInput()
  update()
  render()
}
```

Ne odgovaramo na input nadražaje odmah, već ih samo beležimo:
```js
window.addEventListener("mousedown", e => {
  buttonStates[e.button] = true
})
```

U `handleInput` fazi odgovaramo na uskladištene inpute:
```js
function handleInput() {
  if (buttonStates[LEFT_BUTTON]) {
    player.attacking = true
    delete buttonStates[LEFT_BUTTON]
  }
};
```

Tako kontrolišemo u kojoj će se fazi njihova obrada vršiti, a ne stihijski. Preporučljivo je definisati nazive za tipke, radi čitkosti.

Now we know about the input and can consider it in the update function, knowing that it will adhere to the rest of the game rules.

```js
function update() {
  // If after that the player can still attack, do it!
  if (player.attacking && player.canAttack()) {
    player.attack()
  }
}
```
