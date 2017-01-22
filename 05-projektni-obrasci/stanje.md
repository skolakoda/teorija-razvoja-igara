# Stanje (*state pattern*)

The state pattern implements a state machine in an object-oriented way, by implementing each individual state as a derived class of the state pattern interface, and implementing state transitions by invoking methods defined by the pattern's superclass.

Store game AI as one of several states, eg. Attacking, Wandering, Fleeing. Each can have its own update() method and whatever other data it needs (eg. storing which character it is attacking or fleeing from, the area in which it is wandering, etc.)

The state pattern can be interpreted as a strategy pattern.
