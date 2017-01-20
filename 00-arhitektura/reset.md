# Reset

Reset funkcija služi da vrati scenu na početno stanje, bez korištena grube sile, kao što je osvežavanje browsera.

# Primeri

Primer reset funkcije:
```js
var reset = function () {
	hero.x = canvas.width / 2;
	hero.y = canvas.height / 2;
	// Throw the monster somewhere on the screen randomly
	monster.x = 32 + (Math.random() * (canvas.width - 64));
	monster.y = 32 + (Math.random() * (canvas.height - 64));
}
```
