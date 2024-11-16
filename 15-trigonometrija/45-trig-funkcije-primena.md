#  Primena trigonometrijskih funkcija

Trigonometrijske funkcije su posebno bitne za razvoj igara. Koriste se za računanje rastojanja i ugla ka nekom predmetu, računanje vektora, simulaciju fizike, modelovanje kružnog kretanja, talasa i drugih periodičnih pojava.

## Visina drveta

Bez merenja visine drveta, možemo je izračunati pomoću trigonometrije. Dovoljno je da izaberemo neku tačku, odokativno utvrdimo ugao ka vrhu drveta, i izmerimo rastojanje do podnožja.

![trigonometrija-uzivo](slike/trigonometrija-uzivo.jpg)

Ovde nam može pomoći tangens funkcija:

\[
\tan(\alpha) = \frac{\text{visina}}{\text{rastojanje}}
\]

Pošto je visina nepoznata, menjamo mesta u jednačini:

\[
\text{visina} = \text{rastojanje} \times \tan(\alpha)
\]

## Širina reke

![sirina-reke](slike/sirina-reke.gif)

## Crtanje kruga

Pomoću trigonometrijskih funkcija možemo nacrtati krug:

```js
draw_circle () {
    const length = 50
    const angle_stepsize = 0.1
    let angle = 0.0

    while (angle < 2 * PI) {
      let x = length * cos(angle)
      let y = length * sin(angle)

      draw (x + SCREEN_W / 2, y + SCREEN_H / 2)
      angle += angle_stepsize
  }
}
```

## Kruženje nebeskih tela

Možemo koristiti sinus i kosinus za animaciju orbite planete:

```js
const canvas = document.getElementById('canvas')
const ctx = canvas.getContext('2d')

let angle = 0
const length_x = 100
const length_y = 100

function animate() {
  const x = canvas.width / 2 + length_x * Math.cos(angle)
  const y = canvas.height / 2 + length_y * Math.sin(angle)

  ctx.clearRect(0, 0, canvas.width, canvas.height)
  ctx.fillRect(x - 2, y - 2, 4, 4)

  angle += 0.05
  requestAnimationFrame(animate)
}

animate()
```

## Prateća raketa

Recimo da pišemo igru u kojoj igrač može ispaljivati prateće rakete. Prvo izračunamo vektor razdaljine između rakete i cilja, tako što oduzmemo koordinate rakete od koordinata cilja:

```js
razdaljina.x = target.x − raketa.x
razdaljina.y = target.y − raketa.y
```

Na osnovu ovoga možemo izračunati ugao pod kojim raketa treba da leti, pomoću funkcije `atan2()`:

```js
ugao = atan2(razdaljina.y, razdaljina.x)
```

Ukoliko želimo da raketa prati cilj i nakon lansiranja, potrebno je da povremeno ažuriramo ovaj ugao.