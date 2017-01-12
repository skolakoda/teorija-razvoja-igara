# Projekcija perspektive

3D projekcija je mapiranje trodimenzionalnog prostora na dvodimenzionalnu ravan.

Svet je trodimenzionalan, ali ekran na kome ga prikazujemo je uvek 2D.

![3d-projekcija](slike/3d-projekcija.jpg?row=true)

![perspektiva](slike/perspektiva.png?row=true)

We store 3D coordinates in code. However, a screen can only display 2D coordinates so we need a way to transform our 3D coordinates into 2D ones. The 3D to 2D projection is an abstract math operation, usually made by an object called a virtual camera. This camera converts a 3D coordinates into 2D ones, to send them to the renderer, which will display them on the screen.

Poseban repo:
https://github.com/skolakoda/ucimo-3d-projekciju

Linkovi:
http://alfonse.bitbucket.org/oldtut/Positioning/Tut04%20Perspective%20Projection.html
http://ogldev.atspace.co.uk/www/tutorial12/tutorial12.html
