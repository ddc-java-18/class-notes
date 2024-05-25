# Java Deep Dive: Day 3

Class Date: 22-05-2024

## Topics Covered

- Enums
- Constructors
- Getters & Setters
- Testing

## Github Repos

- [fizz-buzz](https://github.com/ddc-java-18/fizz-buzz-ivan-pd): An application that outputs the first 100 numbers in the Fizz-Buzz children's game.
  - Finished the implementation from day 2.
  - Introduced the `Set` data structure to store unique values in an unordered manner.
  - Used the Java `EnumSet` to store output values from the fizz buzz games.
  - Added parameterized Junit tests to validate fizz-buzz implementation.
- [shuffler](https://github.com/ddc-java-18/shuffler-ivan-pd/commit/2aefe0c7cffaa71cb2b0511fef2f467b38198d4e): A shuffler program that takes in an array of doubles or integers and shuffles the array using the Fisher-Yates Algorithm.
  - Using the Java `RandomGenerator` class.
  - Using a DoubleStream to generate an array or random doubles.
  - How to implement an nested class.
  - How to use an anonymous class.

## Enums

In Java, an `enum` (short for "enumeration") is a special data type that enables for a variable to be a set of predefined constants. The use of enums can make code more readable and less error-prone by ensuring that a variable can only take one out of a small set of possible values.

- Enums give us compiled time safety which is why we use them!
- Enum and their fields should be treated as immutable.
- Default access level for a constructor in an Enum class is private. This is because we don’t want any other classes to make new instances of our Enum values.
- Enums give use built in methods/functionality:

  - `.values()`: Returns an array containing all the constants of the enum in the order they are declared.
  - `.toString()`: Returns the name of this enum constant, as contained in the declaration.
  - `.ordinal()`: Returns the position of the enum constant in its enum declaration.
    - `enum.<VALUE>.ordinal() // gives use the ordinal position`
  - `.compareTo()`: Compares this enum with the specified object for order.
    - `Coin.PENNY.compareTo(Coin.NICKEL)`
  - The following is the equivalent of an enum class. The enum is just syntactic sugar over the following:
  - ```
    class Coin {
        public static final Coin PENNY = new Coin(1, "PENNY");
        public static final Coin NICKEL = new Coin(5, "NICKEL");
        public static final Coin DIME = new Coin(10, "DIME");
        public static final Coin QUARTER = new Coin(25, "QUARTER");

        private final int value;
        private final String name;

        private Coin(int value, String name) {
            this.value = value;
            this.name = name;
        }

        public int getValue() {
            return value;
        }

        public static Coin[] values() {
            return new Coin[] { PENNY, NICKEL, DIME, QUARTER };
        }

        // Used to get a more readable string representation of the object.
        public String toString() {
            return name;
        }
    }

    enum Coin {
        PENNY(1), NICKEL(5), DIME(10), QUARTER(25);

        private final int value;

        Coin(int value) {
            this.value = value;
        }

        public int getValue() {
            return value;
        }
    }
    ```

Enum Sets:

## Constructors

In Java, a constructor is a special type of method that is used to initialize objects. A constructor is called when an instance of a class is created.

- Constructors don’t have a return value and must have the same name as the class they are in.
- To refer to non-static instance fields within a constructor we use the `this` keyword.
- You can make a constructor private such that you can’t make instance outside of its class.
- If a class doesn’t define a constructor, the complier will create a public no parameter constructor in the bytecode. This is called the default constructor.

## Testing

- Annotations are just markers in the code that get stored in the Java bytecode.

  - `@ParameterizedTest` uses an `@ValueSource` annotation to provide a collection of values to test on.
  - `@DisplayName` used to give a test a specific display name that is not the same as its method name.
  - ```
    @ParameterizedTest
      @ValueSource(ints = {33, 72, 3, 99})
      void evaluate_fizz(int value) {
        assertEquals(EnumSet.of(Result.FIZZ), FizzBuzz.evaluate(value));
      }
    ```

- How are instances of test classes made? Junit makes a new instance of the class before each test. This is done so that each test runs in isolation.

  - First the FizzBuzzTest class is loaded into memory (note: the class not an instance of the class is loaded into memory)
  - Junit then looks for annotations in the byte code.
  - If no test annotations are found then no test are run.
  - if test annotations are found
    - Junit invokes the @BeforeAll
    - @BeforeEach run right after each instance initialization
    - @AfterEach: Run after each tests.
    - @AfterAll: Run after all tests.
