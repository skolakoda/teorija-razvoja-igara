# Integracija

Simulacija fizike u igrama radi tako što pravi predviđanja na osnovu zakona fizike. Ova predviđanja izvodimo pomoću matematičke tehnike koja se zove integracija.

Brzina, položaj i ubrzanje tela su blisko povezani. Brzina je promena položaja kroz vreme. Slično, ubrzanje je promena brzine kroz vreme. Povezanost ovih svojstava nam prilično koristi, jer ako znamo prethodne položaje predmeta, možemo saznati njegovu brzinu i ubrzanje. Štaviše, ako znamo ubrzanje, možemo saznati koliko će se brzina menjati svake sekunde. Ako znamo brzinu, možemo saznati koliko će se položaj menjati svake sekunde.

## Ojlerov metod (*Euler*)

Ojlerov metod je najjednostavniji način izvođenja numeričke integracije (procedure rešavanja diferencijalnih jednačina sa datom početnom vrednošću). Računamo ubrzanje, brzinu i položaj (pretpostavka da sve kreće od 0):

```
ubrzanje = sila / masa
brzina += ubrzanje * vremenski_korak (tj. delta_vreme)
položaj += brzina * vremenski_korak
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

http://www.richardlord.net/presentations/physics-for-flash-games
http://genericgamedev.com/general/basic-game-physics-from-newton-to-code/
