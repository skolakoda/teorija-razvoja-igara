# Tvornica / tvornički obrazac (*Factory pattern*)

> omogućuje centralizovano stvaranja i uništavanja objekata (npr. na osnovu konfiguracija iz fajla)

Na primer, strateške igre moraju da stvaraju (*spawn*-uju) na stotine likova za svaki nivo, na osnovu podataka iz json fajla. Tome služi tvornička klasa.

```js
function spawnEntity (typename) {
    const entity = new (factory[typename])()  // dinamicki kreira instancu
    entities.push(entity)
    return entity
}
```

Igre kontinuirano stvaraju i uništavaju objekte. Bilo da su objekti tekstualni blokovi ili neprijatelji, značajan deo programa je posvećen stvaranju na zahtev i uništavanju na kraju životnog ciklusa. Kako mnogi programeri rade na istom kodu, a aplikacije rastu, kod stvaranja-uništavanja se širi na mnoge datoteke, često uzrokujući probleme zbog nesukladnosti u protokolu. Tvornički obrazac centralizuje stvaranje i uništavanje objekata, pružajući univerzalan i siguran način za rukovanje objektima.
