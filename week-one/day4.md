# Java Deep Dive: Day 4

Class Date: 23-05-2024

## Topics Covered

- Class Modeling
- Separations of Concerns & MVC
- SOLID Design Principles + DRY + YAGNI
- Java Records

## Github Repos

* [playing-cards](https://github.com/ddc-java-18/playing-cards-ivan-pd): A java application for a cool card trick.
  * Using a constructor in an `Enum`.
  * Creating Javadoc comments.
  * Using Java Record class.
  * Implementing the `Comparable` interface.

## Notes

- Class Modeling

  - What do we want to leave in and what do we want to include in a class.
  - Class Diagrams are constructed of three parts: the class name, the class attributes, and the class actions/methods.
  - Composition: Has-A Relationship.
  - Inheritance: Is-A Relationship
  - Favor Composition over Inheritance
  - Domain Model
- Separations of Concerns and Model-View-Controller

  - MVC:
    - Model: Internal representation of sate.
    - View: Construction of consumable representations of system state.
    - Controller: Handling of input/events outside the system and performing any necessary manipulation of the model.
  - Android uses MVVM
  - .Net uses Model-View-Presenter
- SOLID Design Principles

  - Single responsibility principle
  - Open-closed Principles
    - If you have planned for a class to not be extendable then makes sure that it cannot be extended.
  - Liskov substitution principle.
  - Interface Segregation Principle
  - Dependency Inversion Principle
    - When possible your code should depend on abstractions.
    - Make you code the most general type that fits your requirements.
- DRY: Don’t repeat yourself
- YAGNI: You ain’t going to need it
- Overriding the `Object` toString method allows us to provide an implementation for how we want our object to be represented as a string.
- Java records

  - class needs to be final and variables need to be final and we want “getters/setters” automatically for us.
  - It will also create a Canonical Constructor
    `Card(Rank rank, Suit suit)`
  - Logic added to the canonical constructor
  - We can add more constructors to the Record class but it must call the canonical constructor using the `this` keyword.

  ```
   public Card(RandomGenerator rng) {
      this(
          Rank.values()[rng.nextInt(Rank.values().length)],
          Suit.values()[rng.nextInt(Suit.values().length)]
      );
    }
  ```
