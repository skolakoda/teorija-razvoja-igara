# Koordinatni sistemi

> If you use the x- and y-coordinates, you are using Cartesian coordinates. If you use the angle and length of the vector, you are using polar coordinates.

## Kartezijanski 2D koordinatni sistem

Kartezijanski (Dekartov) koordinatni sistem se sastoji od horizontalne (`x`) i verticalne (`y`) ose. Svaka tačka može biti određena sa (x,y). Ishodište je tačka u kojoj se ose seku, na koordinatama (0,0).

![dimenzije](slike/dimenzije.png)

Dve česte konvencije za koordinatni sistem su:
* Ishodište je dole levo, sa x osom nadesno i y nagore.
* Ishodište je gore levo, sa x osom nadesno i y nadole.

## Kartezijanski 3D koordinatni sistem

Dekartov 2D koordinatni sistem se lako može proširiti na 3D, dodavanjem treće ose (`z`). Na primer, da bi dospeo do neke tačke, moraš ići 2 jedinice desno, 4 jedinice gore i 5 jedinica napred; to se može opisati nizom (2,4,5).

3D koordinatni sistem može biti "levoruki" i "desnoruki".

![3d-koordinate-prstima](slike/3d-koordinate-prstima.jpg)

![left_right_hand](slike/left_right_hand.gif)

WebGL koristi desnoruki koordinatni sistem — x osa se proteže nadesno, y osa nagore, a z osa van ekrana:

![](slike/webgl-coordinate-system.png)

## Polarni koordinatni sistem

U polarnom koordinatnom sistemu je pozicija tačke određena njenom udaljenošću od ishodišta i uglom. Polarni koordinatni sistem je poseban oblik cilindričnog koordinatnog sistema.

![polarne-koordinate](slike/polarne-koordinate.png)

## Normalizovane koordinate uređaja (*Normalized Device Coordinates*)

Normalized Device Coordinates could range from [-1, 1] for both the x and y axis. A programmer does all screen design in NDC. There are three realities of the hardware that NDC hides from us:
* The actual number of pixels in x and y.
* Non-uniform pixel spacing in x and y.
* Up versus down for the Y coordinate. The NDC-to-pixel transformation will invert Y if necessary so that Y in NDC points up.

If we map directly from WCS to a DCS, then changing our device requires rewriting this mapping. Instead, use Normalized Device Coordinates (NDC) as an intermediate coordinate system that gets mapped to the device layer.

![](slike/ndc.gif)
