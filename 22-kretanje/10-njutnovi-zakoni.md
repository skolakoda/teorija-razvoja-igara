# Njutnovi zakoni kretanja

Isak Njutn je u 17. veku otkrio tri zakona koja regulišu sva kretanja na Zemlji (osim na molekularnom nivou). Najvažniji je Njutnov drugi zakon, koji upravlja gotovo svim interakcijama predmeta u igrama.

The first two laws are implemented in the integration stage, and the third during resolution of collisions.

## Prvi Njutnov zakon (Zakon inercije)

> Svako telo ostaje u stanju relativnog mirovanja ili ravnomernog pravolinijskog kretanja sve dok ga dejstvo drugog tela ne prisili da to stanje promeni.

![](slike/zakon-inercije.gif)

It is the natural tendency of objects to keep on doing what they're doing. Ako se kreće, kretaće se, ako miruje, mirovaće. This specifies scenario when the net force is 0. Međutim, priroda se na razne načine opire kretanju tela.

## Drugi Njutnov zakon (Zakon sile)

>	Ubrzanje je srazmerno primenjenoj sili, a obrnuto srazmerno masi tela.

![](slike/newtons-first-law.png)

Dakle, ubrzanje izaziva sila, a protivi mu se masa:

```
a = F / m
```
odnosno:
```
F = m * a
```

U višedimenzionalnim svetovima (2D i 3D) `F` i `a` su vektori. To znači da možeš računati svaku dimenziju posebno:
```
Fx = m * ax
Fy = m * ay
```
U 3D kretanju postoji i z osa:
```
Fz = m * az
```

## Treći Njutnov zakon (Zakon akcije i reakcije)

>	Sila kojom jedno telo deluje na drugo telo jednaka je po intenzitetu sili kojom drugo telo deluje na prvo, ali je suprotnog smera.

Na primer, kada top ispaljuje projektil, projektil ga pomera nazad.

![](slike/top.gif)
