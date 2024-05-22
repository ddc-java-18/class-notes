# Java Deep Dive: Day 1

Contributers: ivan-pd

Class Date: 20-05-2024

## Topics Covered

- Github Repos (Coding Follow Alongs)
- Java History & Key Components
- Primitive Types & Literals in Java
- Basics of Creating a Java Program
- Building, Compiling, and Running Java

## Github Repos

* [command-line](https://github.com/ddc-java-18/command-line-nick-bennett): A command-line application that accepts a temperature input in Fahrenheit and converts it to its equivalent in Celsius.
  * Learned how arguments are passed from the command line into the Main method through `String[] args`
  * Utilized our first control-flow structure: The enhanced for-loop (aka the for-each loop):

    ```
    for (<current value declaration> : <array or Iterable>) 
        <statement>
    ```
  * Learned how to use a fomated print statement using `System.out.printf()`
  * How to parse strings representations of values into their corresponding primitive type:

    * Example: `Double.parseDouble(arg)` to parse a `String` argument into a primitive `double`
* [temperature-conversion](https://github.com/ddc-java-18/command-line-nick-bennett): A temperature convertion application that can convert temperatures between Celsius, Fahrenheit, and Kelvin.
  * How to create a `.gitignore` file and what it does.
  * Build System Introduction (Gradle)
  * Using an `Enum` Class to switch between temperature conversion modes.
  * Using a `Try-Catch` statement to catch and handle exceptions.

    ```
    try {
        // Code that might throw an exception
    } catch (ExceptionType1 e1) {
        // Handle ExceptionType1
    }
    ```
  * How to create Java constants using `static final`
  * Using Java's new switch statement for branching logic

    ```
    switch (variable) {
        case VALUE1 -> {
           // Code to execute for VALUE1
        }
        case VALUE2 -> 
            // Single statement for VALUE3
            someValue;
        default -> {
            // Code to execute if no cases match
            // This block is optional but recommended for handling unexpected values
        }
    }
    ```

### Java History & Key Components:

* [Deep Dive Doc on Java History](https://ddc-java.github.io/java-timeline/)
* [Deep Dive Doc on JRE, JCL, &amp; JVM
  ](https://ddc-java.github.io/jre-jdk/)

**Important Structure to Remember!!!** 

Java Development Kit:

* Development Tools
  * `javac`: Compiler
  * `javadoc`: Documentation Generator
  * `jshell`: REPL
* Java Runtime Environment
  * Runtime Tools
    * `java`: Application Launcher
  * Java Class Library
    * `java`: Root package for libary core
      * `java.awt`: Abstract Window Toolkit
      * `java.io`: Basic input/output
      * `java.lang`: Core Object types
      * `java.net`: Basic network & addressing
      * `java.math`: Numeric types and operations
      * `java.nio.file`: Filesystem operations
      * `java.util`: Utility classes and interfaces
      * ... So many more packages
  * Java Virtual Machine
    * Just In Time (JIT) Compilation
    * Bytecode Verificaiton
    * Garbage Collection
    * Class Loading

### Primitive Types & Literals

In Java, a primitive type is a basic data type that is built into the language and not derived from any other data type. Primitive types are the most fundamental types of data and are used to represent simple values. Java has eight primitive data types, each designed for a specific kind of data. If you want to re-visit this information see the [DDC Building Blocks](https://ddc-java.github.io/building-blocks/types.html) page.

1. boolean
2. char
3. byte
4. short
5. int
6. long
7. float
8. double

**Literal** : Refers to the fixed values that can be assigned to variables of primitive types.

* **Integer Literals** : Can be assigned to `byte`, `short`, `int`, and `long`.
* **Floating-Point Literals** : Can be assigned to `float` and `double`.
* **Boolean Literals** : Can be assigned to `boolean`.
* **Character Literals** : Can be assigned to `char`.
* **String Literals:** Sequence of characters enclosed in double quotes (the only non-primitive type which has a literal)

### Basics of Creating a Java Program:

* **Java Philosophy:** Write once run anywhere.
  * Java code is written in Java classes.
  * These classes get compiled into Java bytecode.
  * Java bytecode can then be run on any device that has a Java Virtual Machine.
* Compiled Java bytecode can be save in a JAR file (Java Archive File), which is basically a zip file of the .class bycode.
* Every Java program must have an entry point, a place where the Java program starts.
  * This entry point is called the Java main method.
  * The main method has a specific method signature:  `public static void main(String[] args)`.
    * To remember the method signature of the main method remember the following acronym (which is also a nice auto-code generator shortcut in Intellij): `psvm`

### Compiling/Building and Running Java Code:

We can compile and run our code in two ways: using an Integrated Development Enviroment (IDE) with a Java build system or manually using Java command line tools. Using an IDE and a build system like Gradle or Maven is the recommend way to compile and run a Java project.

**Compiling Java Code and Running it with Command Line Tools:**

`javac` : The Java compiler tool. Used to compile our `.java` class files into Java byte code with the `.class` file extension.

* **Example:** `javac -d out src/CommandLine.java`
  * `Usage: javac <options>`` <source files>`
  * Used to compile the `CommandLine.java` file and save the compiled java classes into the `out` directory.
  * `-d` : specifies the output directory where we want to save the compiled byte code.

`java` : The Java application launcher. We use this command to launch our complied java bycode and actually run our application.

* **Example:** `java -cp out CommandLine The quick brown fox`
  * `Usage: java [options] <mainclass> [args...]`
  * `-cp`: Command line flag for “class path”. It tells the `java` command line tool where the classes it needs to run are located.
  * `CommandLine`: The name of the java main class file we we want to run.
  * `The quick brown fox` : The command line arguments passed into the `public static void main` method of the java application. These arguments will be passed in as a `String[]` .
