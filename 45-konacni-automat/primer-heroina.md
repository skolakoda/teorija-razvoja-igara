## Heroina

![heroina](slike/heroina.png)

Implementacija u kodu:

```java
void Heroine::handleInput(Input input)
{
  switch (state_)
  {
    case STANDING:
      if (input == PRESS_B)
      {
        state_ = JUMPING;
        yVelocity_ = JUMP_VELOCITY;
        setGraphics(IMAGE_JUMP);
      }
      else if (input == PRESS_DOWN)
      {
        state_ = DUCKING;
        setGraphics(IMAGE_DUCK);
      }
      break;

    case JUMPING:
      if (input == PRESS_DOWN)
      {
        state_ = DIVING;
        setGraphics(IMAGE_DIVE);
      }
      break;

    case DUCKING:
      if (input == RELEASE_DOWN)
      {
        state_ = STANDING;
        setGraphics(IMAGE_STAND);
      }
      break;
  }
}
```
