## Kompozitni obrazac (Composite pattern)

> make a scene graph of renderable objects

The Composite pattern composes objects into tree like structures representing hierarchies. An example may be a game level where we have a number of different pieces e.g. sub levels, trees, enemies etc. and we want to gather them together in a collection.

![composite-pattern](slike/composite-pattern.gif?row=true)

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
