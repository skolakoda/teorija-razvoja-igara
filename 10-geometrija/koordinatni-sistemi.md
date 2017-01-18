# Koordinatni sistemi
> If you use the x- and y-coordinates, you are using Cartesian coordinates. If you use the angle and length of the vector, you are using polar coordinates.

## Cartesian coordinate system

The Cartesian coordinate system consists of a horizontal (x) and a vertical (y) axis. Each individual point can be defined by (x,y). The origin is the point where the two axes intersect; its coordinates are (0,0).

![dimenzije](slike/dimenzije.png)

## 3D

2D coordinate system can be extended to 3D as well. All you have to do is add a third axis (z). 3d koordinatni sistem može biti "levoruki" i "desnoruki". Mi ćemo uglavnom koristiti desnoruki.

To get to point P, you must travel two units to the right, four units up, and five units forward; so the point can be described by the ordered triple (2,4,5).

![3d-koordinate-prstima](slike/3d-koordinate-prstima.jpg)

![left_right_hand](slike/left_right_hand.gif)

WebGL uses the right-hand coordinate system — the x axis points to the right, the y axis points up, and the z axis points out of the screen, as seen in the diagram:

![](slike/webgl-coordinate-system.png)

## Polarni koordinatni sistem

Polarni koordinatni sistem je sistem gde je pozicija tačke određena njenom udaljenošću od fiksne tačke (ishodišta) i uglom. Ishodište se naziva pol. Polarni koordinatni sistem je specijalni oblik Cilindričnog koordinatnog sistema.

![polarne-koordinate](slike/polarne-koordinate.png)

## Koordinate sveta i koordinate kamere

![svet-i-kamera-koordinati](slike/svet-i-kamera-koordinati.png)

Our world origin is located at the lower-left corner of the example program’s window with positive
x pointing to the right and positive y pointing up.

## Normalized Device Coordinates

Two common conventions for DCS:
* Origin in the lower left corner, with x to the right and y upward.
* Origin in the top left corner, with x to the right and y downward.
Takođe, Normalized Device Coordinates could range from [-1, 1] for both the x and y axis.

A programmer does all screen design in NDC. There are three realities of the hardware that NDC hides from us:
* The actual number of pixels in x and y.
* Non-uniform pixel spacing in x and y.
* Up versus down for the Y coordinate. The NDC-to-pixel transformation will invert Y if necessary so that Y in NDC points up.

If we map directly from WCS to a DCS, then changing our device requires rewriting this mapping (among other changes). Instead, use Normalized Device Coordinates (NDC) as an intermediate coordinate system that gets mapped to the device layer.

![](slike/ndc.gif)
