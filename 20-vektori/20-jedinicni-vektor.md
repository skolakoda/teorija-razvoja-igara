# Jedinični vektor (normalizacija vektora)

![](slike/unit-vector.gif)

Jedinični vektor je vektor dužine 1. Možemo normalizovati bilo koji vektor u jedinični vektor istog smera. Da bismo normalizovati vektor, podelimo svaku komponentu sa dužinom vektora:

```
jedinicni_vektor = (vektor.x, vektor.y, vektor.z) / duzina_vektora
```

Na primer, da bismo normalizovali vektor (3,4), delimo svaku komponentu njegovom dužinom 5 i dobijamo (3/5, 4/5). x osa jediničnog vektora se obično naziva `i`, y osa `j`, a z osa `k`.

U igrama, kada radimo sa smerovima (nasuprot položaja i brzina), bitno je da budu jedinične dužine. Na primer, top uperen u smeru (1,0) ispaljuje projektil pri brzini 20 m/s. Koja je vektorska brzina projektila? Obzirom da je dužina 1, jednostavno pomnožimo brzinu projektila da dobijemo vektorsku brzinu: (20,0).

# Normalni vektori

Vektori su normalni u odnosu na površinu kada su pod pravim uglom. Normalni vektori nemaju nikakve veze sa normalizacijom vektora.
