# Java Deep Dive: Day 2

Class Date: 21-05-2024

## Topics Covered

- Github Repos (Coding Follow Along)
- Java String Builder
- Java Input/Output (I/O)
- Regular Expressions
- Unit Testing

## Github Repos

- [temperature-conversion](https://github.com/ddc-java-18/temperature-conversion-nick-bennett): A temperature conversion application that can convert temperatures between Celsius, Fahrenheit, and Kelvin.
  - Continuation from Day 1
  - How to use a Scanner to read input from a file.
  - How to use a regular expression to match a specific pattern.
- [fizz-buzz](https://github.com/ddc-java-18/fizz-buzz-ivan-pd): An application that outputs the first 100 numbers in the Fizz-Buzz children's game. Fizz is outputted if a number is divisible by 3, Buzz is outputted if a number is divisible by 5, and Fizz Buzz is outputted if the number is divisible by 3 and 5.
  - How to use the modulo operator to find the remainder in items
  - Syntax and use of the traditional for-loop
  - Using a `StringBuilder` to concatenate different strings.
  - Using a Ternary Operator for conditional logic.

## Java String Builder

We often find ourselves having to concatenate different strings together to create a new output string to print or for multiple other reasons. However, in Java Strings are immutable objects. This means that when we concatenate we create a new instance of our strings. In addition string concatenation using the `+` isn't very efficient. To solve these issues, we use the Java `StringBuilder` class.

[Java Docs for `StringBuilder`](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/lang/StringBuilder.html)

- `StringBuilder` instances are mutable, meaning you can modify the contents of the string without creating a new object each time, which can be useful for building or modifying strings dynamically.
- `StringBuilder` class is optimized for building strings efficiently, especially when dealing with large amounts of text or frequent string manipulations.

We can create a `StringBuilder` object: `StringBuilder result = new StringBuilder();`

- Use the `.append()` method to concatonate two Strings together: `result.append("buzz")`

## Java Input/Output

To enhance our applications we would like to take input from an external source to our applications like a file. Similarly, we would like to output or save our programs results outside of memory in an external file. To do this, we leverage the use of the Java I/O library to take in input from a Java Stream and output to an external output.

Remember that there are three main Java Streams we use: Standard.in to take in input, Standard.out to output information, ad Standard.error to output errors.

In addition to the main in/out Streams we can also create input and output streams to external files using the Java I/O library.

A common way to get input from a user is to use the Java `Scanner` object. This object has a variety of different methods to read input of different types and length.

A very basic way to read input is to use the `.hasNext()` method to check if our input stream has a next input. We can then use a variation of the `.next()` method to get the next item from the Scanner object.

## Regular Expressions

A regular expression is in simple term just a pattern matcher. It lets use find values that match a pattern that we provide. In class we used a regular expression along with the `Scanner` object to see in an input matched from a file stream with our temperature mode Enum:

```
// From TemperatureConverter.java
if (scanner.hasNext(Mode.PATTERN)) {
        mode = Mode.valueOf(scanner.next(Mode.PATTERN).toUpperCase());
        System.out.printf("Change mode to %s%n", mode);
)

// From Mode.java
public enum Mode {

  CF, FC, CK, KC, KF, FK;

  public static final Pattern PATTERN = Pattern.compile("CF|CK|FC|FK|KC|KF", Pattern.CASE_INSENSITIVE);

}
```

# Unit Testing

- A unit test is supposed to test a "unit" of our code.
- For Java code we use the JUnit testing framework.
  - JUnit uses specialized annotations to recognize tests
- We use Assertions to check if something, a value we want to test, matches it's expected value.

  - In JUnit we use some variation of `AssertEquals` method to do this.

    ```

    class FizzBuzzTest {

      @ParameterizedTest

      @ValueSource(ints = {33, 72, 3, 99})

      void evaluate_fizz(int value) {

        assertEquals("fizz", FizzBuzz.evaluate(value));

      }

    }
    ```

* Note: We write our tests in a mirrored package structure as our "regular" java code. For example, we wrote FizzBuzz in `src/java/main/edu/cnm/deepdive/FizzBuzz.java` so our test class is put in `src/test/java/main/edu/cnm/deepdive/FizzBuzz.jav`
