## Tablica prelaza stanja

Tablica prelaza stanja (*state transition table*) je istinosna tablica koja prikazuje promene stanja konačnog automata, zavisno od trenutnog stanja i ulaza.

### Primer: Neprijatelj

![tablica-stanja](slike/tablica-stanja.png?raw=true)

Implementacija u C++ kodu:

```c++
switch (CurrentState) {
  case RunAway:
    EvadeEnemy();
    if (Safe()) {
      ChangeState(Patrol);
    }
    break;
  case Patrol:
    FollowPatrolPath();
    if (Threatened()) {
      if (StrongerThanEnemy()) {
        ChangeState(Attack);
      } else {
        ChangeState(RunAway);
      }
    }
    break;
  case Attack:
    if (WeakerThanEnemy()) {
      ChangeState(RunAway);
    } else {
      BashEnemyOverHead();
    }
    break;
}
```
