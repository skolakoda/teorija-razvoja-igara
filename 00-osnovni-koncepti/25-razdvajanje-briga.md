# Razdvajanje briga

The World should not draw itself; the Renderer should draw the World. The Player should not draw itself; the Renderer should draw the Player relative to the World. Here is how a typical rendering engine handles these things:

## Drawing an object (*Renderer class*)

You typically have a Renderer class that does this. It simply takes an object and draws in on the screen. It can have methods like drawSprite(Sprite), drawLine(..), drawModel(Model), itd. It also uses any API you have underneath so you can have a renderer that uses WebGL and one that uses Canvas. If you want to port your game to another platform, you simply write a new renderer and use that one.

## Moving an object (*SceneNode class*)

In most game engines a Scene is a graph (tree) of components. Every scene object is a node in a tree. Each object is attached to something we refer to as a SceneNode. A scene node is just a container for mesh objects, with all the transformations (position, rotation, scale) of an object (usually relative to another SceneNode).

## Managing the objects (*SceneManager class*)

SceneNodes are managed through a SceneManager. This class creates and tracks every SceneNode in your scene. You can ask it for a specific SceneNode (usually identified by a string name like "Player" or "Table") or a list of all the nodes.

## Drawing the world (*Renderer class*)

Simply walk through every SceneNode in the scene and have the Renderer draw it in the right place.

## Collision Detection

Usually you can query the Scene about what object is at a certain point, or what objects will a ray intersect. You can then choose to move the player to the new position, move it by a smaller amount (next to the colliding object) or not to move. These queries should be handled by separate classes - the SceneManager only creates and stores nodes.
