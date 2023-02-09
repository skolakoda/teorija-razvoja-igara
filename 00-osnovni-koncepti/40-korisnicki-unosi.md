# Upravljanje unosima (*Input Manager class*)

The first important difference from web development is that the input events doesn't actually do anything right away. If a user presses a key in a typical web app, it makes sense to immediately perform the desired action. But in a game, things have to happen in chronological order to flow correctly.

Obično se inputi obrađuju na početku game loop-a:

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

Nakon što smo registrovali i obradili korisnički unos, možemo ga upotrebiti u igri:

```js
function update() {
  if (player.attacking && player.canAttack()) {
    player.attack()
  }
}
```
