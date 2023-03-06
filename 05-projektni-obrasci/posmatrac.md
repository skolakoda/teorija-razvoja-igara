# Posmatrač (*Observer Pattern*)

U igri, naše klase treba da budu labavo povezane. To znači da mogu da razgovaraju, ali sa malo znanja jedna o drugoj. Labavo povezane klase čine igru modularnom i fleksibilnom za razvoj.

![](slike/observer.jpeg)

Model posmatrača se obično implementira kada subjekat želi da šalje poruke svojim posmatračima. Subjekt ne treba da zna ništa o tome kako rade posmatrači.

Model posmatrača je široko rasprostranjen - Java ga je stavila u osnovnu biblioteku (java.util.Observer), a C# ugradio direktno u jezik (ključna reč event).

Recimo da dodajemo sistem dostignuća u našu igru. Model posmatrača omogućava jednom modulu da objavi da se nešto zanimljivo dogodilo, bez da brine ko prima obaveštenje.
