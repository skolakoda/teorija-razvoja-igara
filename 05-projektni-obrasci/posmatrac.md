# Observer Design Pattern

> have the renderable representation of a character, listen to events from the logical representation, in order to change the visual presentation when necessary, without needing to know anything about rendering code

In a game, all of your classes should be loosely coupled. This means that your classes should be able to interact with each other, but have little knowledge of each other. Making your classes loosely coupled makes your game modular and flexible to add features without adding unintended bugs.

This pattern is normally implemented when an object wants to send messages to its subscriber (other objects). The object does not need to know anything about how the subscribers work, just that they can communicate.

![](slike/observer.jpeg)

Observer is so pervasive that Java put it in its core library (java.util.Observer) and C# baked it right into the language (the event keyword).

Say we’re adding an achievements system to our game. Observer pattern lets one piece of code announce that something interesting happened without actually caring who receives the notification.
