# Delta vreme

Delta vreme je trajanje prethodnog kadra. Zavisi od brzine računara i količine računanja u datom trenutku igre. Obzirom da trajanje kadrova varira, animacija je brža kad su kadrovi kraći, a sporija kad su kadrovi duži.

Delta vreme se koristi kao korektor da bi animacija bila nezavisna od učestalosti kadrova (*frame rate*):

```cs
public float speed = 8f;

void Update ()
{
    transform.position += new Vector3(speed * Time.deltaTime, 0.0f, 0.0f);
}
```
