## 3d scena

A scene graph is a dynamic data structure, similar to a multiway tree. Each node represents an object in a 3D world or perhaps an instruction to the renderer. Every node can have zero or more children nodes.

The scene graph is traversed every frame to draw the visible world.

every object in a 3D universe needs a transform matrix.

For example, imagine a boat with people on it. When the boat moves, all the people on the boat move with it. Their position and orientation stay the same relative to the boat.

This effect is done by concatenating matrices. Every node in the hierarchy has a matrix that describes position and orientation relative to its parent node.

### The Scene Class

The top-level management of the entire scene node hierarchy rests in the capable hands of the Scene class. It serves as the top-level entry point for updating, rendering, and adding new SceneNode objects to the scene hierarchy.
