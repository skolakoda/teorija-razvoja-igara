# Integracija

Simulacija fizike u igrama radi tako što pravi predviđanja na osnovu zakona fizike. Ova predviđanja izvodimo pomoću matematičke tehnike koja se zove integracija.

Brzina (v), položaj (x) i ubrzanje (a) tela su blisko povezani: 
- **brzina** (*velocity*) je promena položaja tokom vremena (v = dx / dt). 
- **ubrzanje** (*acceleration*) je promena brzine kroz vreme (a = dv / dt). 

Povezanost ovih svojstava nam prilično koristi, jer ako znamo prethodne položaje predmeta, možemo saznati njegovu brzinu i ubrzanje. Štaviše, ako znamo ubrzanje, možemo saznati koliko će se brzina menjati svake sekunde. Ako znamo brzinu, možemo saznati koliko će se položaj menjati svake sekunde.

## Ojlerov metod (*Euler*)

Ojlerov metod je najjednostavniji način izvođenja numeričke integracije (rešavanja diferencijalnih jednačina sa datom početnom vrednošću). Računamo ubrzanje, brzinu i položaj (pretpostavka da sve kreće od 0):

```
ubrzanje = sila / masa
brzina += ubrzanje * delta_vreme (promena brzine)
položaj += brzina * delta_vreme (promena polozaja)
```

Možemo prvo ažurirati položaj pa brzinu, ili obratno. Prvi je eksplicitni Ojlerov metod:

```
x += v * dt
v += (1/m * F) * dt
```

Drugi je poluimplicitni Ojlerov metod (*symplectic Euler*):

```
v += (1/m * F) * dt
x += v * dt
```

Ove jednostavne jednačine su sve što nam treba da pomeramo predmete sa linearnom brzinom i ubrzanjem.

### Primer

Na telo u mirovanju, težine jedan kilogram, primenjujemo konstantnu silu od 10 njutna u vremenskim koracima od jedne sekunde:

```js
const mass = 1
const force = 10
const dt = 1

let t = 0
let velocity = 0
let position = 0

while (t < 10) {
  position = position + velocity * dt
  velocity = velocity + (force / mass) * dt
  t += dt

  console.log(`t=${t}:    position = ${position}      velocity = ${velocity}`)
}
```

Rezultat:
```
t=1:    position = 0       velocity = 10
t=2:    position = 10      velocity = 20
t=3:    position = 30      velocity = 30
t=4:    position = 60      velocity = 40
t=5:    position = 100     velocity = 50
t=6:    position = 150     velocity = 60
t=7:    position = 210     velocity = 70
t=8:    position = 280     velocity = 80
t=9:    position = 360     velocity = 90
t=10:   position = 450     velocity = 100
```

## Verle integracija (*Verlet*)

Euler’s method is great for a conceptual understanding, but it’s not quite accurate. We’ll go a step further and use velocity Verlet integration. Instead of the above, we can do the following:

```
proslo_ubrzanje = ubrzanje
položaj += brzina * vremenski_korak + (0.5 * proslo_ubrzanje * vremenski_korak^2)
novo_ubrzanje = sila / masa
prosecno_ubrzanje = (proslo_ubrzanje + novo_ubrzanje) / 2
brzina += prosecno_ubrzanje * vremenski_korak
```

Glavna prednost Verle metode je upotreba prosečnog ubrzanja između dva kadra, što značajno povećava preciznost.

# Primena u igrama

Proces simulacije kretanja tela izgleda otprilike ovako:
<!-- * izračunaj svojstva mase za predmet (masa, centar mase, momenat inercije) -->
* ustanovi koje sile deluju na predmet
* saberi sile da dobiješ rezultantu ili ukupnu silu
* koristi `F = m * a` da izračunaš ubrzanje tela na osnovu sile (linearno i ugaono ubrzanje)
* korist ubrzanje tela da izračunaš brzinu (linearnu i ugaonu brzinu)
* koristi brzinu tela da izračunaš položaj (linearni i ugaoni pomeraj)
* pošto se dejstvujuće sile menjaju, neprestano ponavljaj ovaj proces

Instead of drowning in maths, you could simulate physics. For every object every step:

```
apply gravity  (add constant to velocity)
apply velocity (add velocity to position)

if (position > some limit) {
    reverse velocity
    multiply velocity by "bounciness" between 0 and 1
    if velocity < 0.5
      set velocity and gravity to 0
}
```

http://www.richardlord.net/presentations/physics-for-flash-games
http://genericgamedev.com/general/basic-game-physics-from-newton-to-code/
https://gafferongames.com/post/integration_basics/