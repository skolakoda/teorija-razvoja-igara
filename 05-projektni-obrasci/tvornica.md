# Tvornica (*Factory pattern*)

> create NPCs or GUI widgets based on a string read from a file

Strategije moraju da spawn-uju na stotine likova za svaki nivo, na osnovu podataka iz json fajla. Tome služi Tvornica klasa.

```js
gGameEngine.spawnEntity = function (typename) {
    const entity = new (gGameEngine.factory[typename])()  // dinamicki poziva funkciju
    gGameEngine.entities.push(entity)
    return entity
}
```

Games tend to build complex objects, such as controls or sprites, and store them in lists or other collections.

Games need to create and dispose of objects continually. Whether objects are text blocks in a word processor or enemies in a hack-and-slash game, a significant portion of your program is surely devoted to creating them on demand and destroying them at the end of their life cycle. As many programmers work on the same code and applications grow, this creation-destruction code spreads through many files, often causing problems due to inconsistencies in the protocol. The factory pattern centralizes the object creation and destruction, thus providing a universal, rock-solid method for handling objects.
