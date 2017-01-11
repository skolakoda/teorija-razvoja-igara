## Projektni obrasci

### Fasadni obrazac

Služi kao posrednik između dva podsistema.

![bad-coupling](slike/bad-coupling.png?row=true)

![facade-pattern](slike/facade-pattern.png?row=true)

### Singleton

A singleton is a global object for which only one instance exists in the whole application. All games need global objects that must be visible from many different classes and scopes. A texture manager, the joystick controller object, and the player class are all singletons.

It starts by declaring a class that has only one public method, which will be used to request an instance of the singleton. All instances actually point at the same structure, so this request call must create the singleton for the first call and just return pointers to it in subsequent calls.

### Strategy

Sometimes you will need to create objects whose behavior can be changed dynamically. Take a soldier, for example. He might have an update routine that recalculates all his AI. Imagine that his AI can be one of four types: an AI routine to fight, one to escape, one to stay idle, and one to follow a trajectory with his squad mates.

Here is where the strategy pattern kicks in. Its goal is to separate the class definition from one (or several) of its member algorithms, so these algorithms can be interchanged at runtime.

The implementation of the strategy pattern involves two classes. First, there is the strategy class, which provides the strategic algorithm. This is a pure abstract class, from which specific strategies are derived as subclasses. Second, there is the context class, which defines where the strategy should be applied and has a member that executes the selected strategy and swaps strategies when needed.

### Factory

Games tend to build complex objects, such as controls or sprites, and store them in lists or other collections.

Games need to create and dispose of objects continually. Whether objects are text blocks in a word processor or enemies in a hack-and-slash game, a significant portion of your program is surely devoted to creating them on demand and destroying them at the end of their life cycle. As many programmers work on the same code and applications grow, this creation-destruction code spreads through many files, often causing problems due to inconsistencies in the protocol. The factory pattern centralizes the object creation and destruction, thus providing a universal, rock-solid method for handling objects.

### Composite

Many types of applications, games in particular, need to hold heterogeneous collections of data together. A game level can have sublevels, potions, enemies, objects, and so on. The overall data structure can be best described as a part-whole hierarchy with each element being either a primitive or a composite. Having all data in a single structure makes traversal more intuitive. This is what the composite pattern is all about: creating part-whole heterogeneous hierarchies where we can access primitives and composite objects using a standard interface.

As an example, the class Level represents the whole level, and then we use the class LevelItem to describe primitive entities inside that level: potions, objects the user can grab, and so on:

```java
class Level {
  public:
    virtual ~Level();
    const char* Name() { return _name; }
    virtual float LifePoints();
    virtual int NumEnemies();
    virtual void Add(LevelItem*);
    virtual void Remove(LevelItem*);
    virtual Iterator<LevelItem*>* CreateIterator();
  protected:
    LevelItem(const char*);
  private:
    const char* _name;
};

class Potion: public LevelItem {
  public:
    Potion(const char*);
    virtual ~Potion ();
    virtual float LifePoints();
};

class CompositeItem : public LevelItem {
  public:
    virtual ~CompositeItem();
    virtual float LifePoints();
    virtual int NumEnemies();
    virtual void Add(LevelItem*);
    virtual void Remove(LevelItem*);
    virtual Iterator<LevelItem*>* CreateIterator();
  protected:
    CompositeItem(const char*);
  private:
    List<LevelItem*> _items;
};

float CompositeItem::LifePoints() {
    Iterator<LevelItem*>* i = CreateIterator();
    float total = 0;
    for (i->First(); !i->IsDone(); i->Next()) {
        total += i->CurrentItem()->LifePoints();
    }
    delete i;
    return total;
}

int CompositeItem::NumEnemies() {
    Iterator<LevelItem*>* i = CreateIterator();
    int total = 0;
    for (i->First(); !i->IsDone(); i->Next()) {
        total += i->CurrentItem()->NumEnemies();
    }
    delete i;
    return total;
}

class Enemy : public CompositeItem{
  public:
      Enemy(const char*);
      virtual ~Enemy();
      virtual float LifePoints();
      virtual int NumEnemies();
};

class SubLevel: public CompositeItem{
  public:
      SubLevel(const char*);
      virtual ~SubLevel();
      virtual float LifePoints();
      virtual int NumEnemies();
};

void LordOfTheRings () {
  Level* MiddleEarth=new Level("Middle Earth");
  SubLevel* TheShire= new SubLevel("TheShire");
  SubLevel* Moria= new SubLevel("Mines of Moria");
  MiddleEarth->Add(TheShire);
  MiddleEarth->Add(Moria);
  Enemy *Nazgul=new Enemy("Nazgul");
  Enemy *NazgulRider=new Enemy("NazgulRider");
  Enemy *NazgulSteed=new Enemy("NazgulSteed");
  Nazgul->Add(NazgulRider);
  Nazgul->Add(NazgulSteed);
  TheShire->Add(Nazgul);
  Enemy *Balrog=new Enemy("Balrog");
  Moria->Add(Balrog);
  Potion *Lembas=new Potion("Lembas");
  TheShire->Add(Lembas);
  cout << "The number of monsters in Middle Earth is " << MiddleEarth->NumEnemies() << endl;
  cout << "The life points for the monsters are " << MiddleEarth-
  >LifePoints() << endl;
}
```

This code creates a hierarchy based on The Lord of the Rings. As a result, we create two sublevels (Moria and The Shire) and then a host of creatures and potions in each zone.
