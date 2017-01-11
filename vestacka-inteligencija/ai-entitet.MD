## AI entitet

Postoje dva tipa entiteta veštačke inteligencije. The first is the agent, which is a game character (some creature). The second type of AI entity is abstract controllers. Take a strategy game, for example. Abstract entity provides the tactical reasoning that acts like the master controller of the CPU side of the battle.

These AI systems are structured in a way similar to our brain. It is easy to identify four elements or rules:
* A sensor or input system
* A working memory
* A reasoning/analysis core
* An action/output system

### Sensing the World

All AIs need to be aware of their surroundings so they can use that information in the reasoning/analysis phase.

In Quake, an individual enemy needs to know:
* Where is the player and where is he looking?
* What is the geometry of the surroundings?
* Sometimes, which weapons am I using and which is he using?

Master controller in a strategy game, such as Age of Empires, needs to know:  
* What is the balance of power in each subarea of the map?
* How much of each type of resource do I have?
* What is the breakdown of unit types: infantry, cavalry, and so on?
* What is my status in terms of the technology tree?
* What is the geometry of the game world?

In many scenarios, sensing the game world (analyzing maps and extracting information) is the slowest part of the AI.

### Memory

Storing AI data is often complex because the concepts being stored are not straightforward. In an individual level AI, this will be less of a problem. We can store points and orientations and use numeric values to depict the "state" the AI is in. If the character is walking, the state equals one; if he's running, the state equals two; and so on.

### Reasoning Core

The analysis/reasoning core is what people often think about when they talk about AI. It is the part that uses the sensory data and the memory to analyze the current configuration and make a decision. Popular methods for such tasks are finite state machines and rule systems. Luckily, games usually require simple decision-making processes involving a few choices, and great results often come at a relatively low price.

### Action/Output System

Intelligence, no matter how sophisticated, must permeate actions and responses. In fact, many games exaggerate this action system much like in a theater play, so the character's intentions are obvious and personality is conveyed.

As an example, recall the Super Mario Bros game. All types of crazy creatures filled the game world, from turtles to lizards and many other creatures. If you separate logic from the actual actions, you'll discover that these AIs were all very similar. But by creating "signature" movements for each one of them, personality and perceived intelligence was enhanced.
