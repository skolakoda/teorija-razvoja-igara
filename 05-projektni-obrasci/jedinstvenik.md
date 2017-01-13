## Jedinstvenik (Singleton)

A singleton is a global object for which only one instance exists in the whole application. All games need global objects that must be visible from many different classes and scopes. A texture manager, the joystick controller object, and the player class are all singletons.

It starts by declaring a class that has only one public method, which will be used to request an instance of the singleton. All instances actually point at the same structure, so this request call must create the singleton for the first call and just return pointers to it in subsequent calls.

![](slike/sington.png)
