# Scena kao graf

Graf scene je dinamička struktura podataka, slična višestrukom stablu. Svaki čvor predstavlja objekat u svetu igre ili možda instrukciju rendereru. Svaki čvor može imati nula ili više podčvorova.

Graf scene se prolazi (*traverse*) svaki kadar da bi se nacrtao vidljivi svet.

Svaki objekat u 3D univerzumu treba transformacionu matricu. Na primer, zamislite brod sa ljudima na njemu. Kada se brod kreće, svi ljudi na brodu se kreću zajedno sa njim. Njihov položaj i orijentacija ostaju isti u odnosu na brod. Ovaj efekat se postiže spajanjem matrica. Svaki čvor u hijerarhiji ima matricu koja opisuje položaj i orijentaciju u odnosu na njegov roditeljski čvor.

# Klasa Scena

Upravljanje hijerarhijom čvorova se nalazi u rukama klase Scena. Ona služi kao ulazna tačka za ažuriranje, renderovanje i dodavanje novih čvorova hijerarhiji scene.

# Klasa Scena i fizika

The Scene class acts as a container for everything involving a physics simulation scenario. It calls and uses the results of any broad phase, contains all rigid bodies, runs collision checks and calls resolution.

Here is an example of what a scene structure may look like:

Klasa Scena deluje kao kontejner za sve što se tiče simulacije fizike. Ona poziva i koristi rezultate široke faze detekcije sudara, sadrži sve čvrste tela, pokreće provere sudara i poziva razrešenja.

Primer kako može izgledati struktura scene:

```java
class Scene
{
private:
  float dt;     // in seconds
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

Ideja je da se korisniku omogući da lako dodaje i uklanja čvrsta tela. 
* Struktura `BodyDef` sadrži sve informacije o čvrstom telu. 
* Funkcija `Step()` izvršava jednu rundu provera sudara, razrešenja i integracije. Poziva se iz glavne petlje. 
* Funkcija `QueryPoint` ili `QueryAABB` proverava koja objekti se zapravo sudaraju, ili sa pokazivačem ili sa AABB.
