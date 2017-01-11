### Linearna jednačina

Linearna jednačina se grafički može predstaviti pravom linijom. Primer:
```
y = 2x
```
So, every straight line is an equation of the form `Ax + By = C`, where A and B are not both 0.

![linearna-jednacina](slike/linearna-jednacina.png?row=true)

One of the most important elements of a line is its slope (nagib).

### Applications in Collision Detection

There will be times in game programming when you'll want to know if and where two lines intersect. The lines might represent two walls. After you set the equations of these lines, you can put the two equations together to form a system of linear equations. Then you can solve the system mathematically.

When solving a system of two linear equations, you're really searching for the intersection of two lines. The solution set is the set of all the points that satisfy both equations.

![presek-linija](slike/presek-linija.png?row=true)

Dve linije se mogu seći ili ići jedna preko druge ili biti paralelne.

A system of two linear equations in the same plane has:
* Exactly one solution if the two graphs have different slopes.
* An infinite set of solutions if both graphs have the same slope and y-intercept.
* No solution if the graphs have the same slope but different y-intercepts.
