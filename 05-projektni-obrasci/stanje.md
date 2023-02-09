# Stanje (*state pattern*)

Obrazac stanja implementira mašinu stanja na objektno-orijentisan način, tako što implementira svako pojedinačno stanje kao izvedenu klasu od interfejsa obrasca stanja, i implementira prelaze stanja pozivanjem metoda superklase.

Svako stanje može imati svoju `update()` metodu i bilo koje druge potrebne podatke (npr. lika koji juri, oblast kojom luta, itd.). AI igru čuvamo kao jedno od nekoliko stanja, npr. napadanje, lutanje, bežanje. 

Obrazac stanja može se tumačiti kao model strategije.