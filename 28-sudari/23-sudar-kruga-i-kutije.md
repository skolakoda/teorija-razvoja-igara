# Otkrivanje sudara kruga i kutije

Test for collision at rect corner
* Think of a line from the rect center to any rect corner
* Now extend that line by the radius of the circle
* If the circle’s center is on that line they are colliding at exactly that rect corner

Heres the full code:
```js
// define a circle and a rectangle
var circle = {x:100, y:290, r:10}
var rect = {x:100, y:100, w:40, h:100}

function RectCircleColliding(circle,rect){
    // find the vertical & horizontal (distX/distY) distances between the circle’s center and the rectangle’s center
    var distX = Math.abs(circle.x - rect.x-rect.w/2)
    var distY = Math.abs(circle.y - rect.y-rect.h/2)

    // if the distance is greater than halfCircle + halfRect, then they are too far apart to be colliding
    if (distX > (rect.w/2 + circle.r)) return false
    if (distY > (rect.h/2 + circle.r)) return false

    // If the distance is less than halfRect then they are definitely colliding
    if (distX <= rect.w/2) return true
    if (distY <= rect.h/2) return true

    // using Pythagoras formula to compare the distance between circle and rect centers
    var dx = distX - rect.w/2
    var dy = distY - rect.h/2
    return (dx*dx + dy*dy <= circle.r * circle.r)
}
```

http://jsfiddle.net/m1erickson/n6U8D/
