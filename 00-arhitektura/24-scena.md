# Graf Scena

A scene graph is a dynamic data structure, similar to a multiway tree. Each node represents an object in a game world or perhaps an instruction to the renderer. Every node can have zero or more children nodes.

The scene graph is traversed every frame to draw the visible world.

Every object in a 3D universe needs a transform matrix. For example, imagine a boat with people on it. When the boat moves, all the people on the boat move with it. Their position and orientation stay the same relative to the boat.

This effect is done by concatenating matrices. Every node in the hierarchy has a matrix that describes position and orientation relative to its parent node.

# Klasa Scena

The management of the node hierarchy rests in the hands of the Scene class. It serves as the entry point for updating, rendering and adding new nodes to the scene hierarchy.

# Klasa Scena i fizika

The Scene class acts as a container for everything involving a physics simulation scenario. It calls and uses the results of any broad phase, contains all rigid bodies, runs collision checks and calls resolution.

Here is an example of what a scene structure may look like:

```java
class Scene
{
private:
  float dt;     // Timestep in seconds
  LinkedList body_list;
  int body_count;
  Vec2 gravity;

public:
  void SetDT(real dt);
  float GetDT(void);

  Body *CreateBody(ShapeInterface *shape, BodyDef def);
  // add a body into the scene and initializes the body (computes mass)
  void AddBody(Body *body);
  void RemoveBody(Body *body);

  // updates the scene with a single timestep
  void Step(void);

  LinkedList *GetBodyList(void);
  void QueryAABB(CallBackQuery cb, const AABB& aabb);
  void QueryPoint(CallBackQuery cb, const Point2& point);
};
```

The idea is to allow the user to add and remove rigid bodies easily. The `BodyDef` is a structure that holds all information about a rigid body. `Step()` function performs a single round of collision checks, resolution and integration. Should be called from the main loop. `QueryPoint` or `QueryAABB` involves checking to see which objects actually collide with either a pointer or AABB within the scene.
