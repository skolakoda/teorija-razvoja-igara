## Koordinate sveta i koordinate kamere

![svet-i-kamera-koordinati](slike/svet-i-kamera-koordinati.png)

Our world origin is located at the lower-left corner of the example program’s window with positive x pointing to the right and positive y pointing up.

## Normalizovane koordinate uređaja (*Normalized Device Coordinates*)

Normalized Device Coordinates could range from [-1, 1] for both the x and y axis. A programmer does all screen design in NDC. There are three realities of the hardware that NDC hides from us:
* The actual number of pixels in x and y.
* Non-uniform pixel spacing in x and y.
* Up versus down for the Y coordinate. The NDC-to-pixel transformation will invert Y if necessary so that Y in NDC points up.

If we map directly from WCS to a DCS, then changing our device requires rewriting this mapping. Instead, use Normalized Device Coordinates (NDC) as an intermediate coordinate system that gets mapped to the device layer.

![](slike/ndc.gif)

http://alfonse.bitbucket.org/oldtut/Positioning/Tutorial%2007.html
