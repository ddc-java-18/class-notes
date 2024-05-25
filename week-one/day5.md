# Java Deep Dive: Day 4

Class Date: 24-05-2024

## Topics Covered

- Primitives and how Objects are passed by Reference.
- How methods are stored on the Stack in Stack Frames.
- Garbage Collector.
- Strategy Design Pattern.
- Java Lists
- Unchecked vs Checked Exceptions
- REST
- Java Iterable and Iterator Interfaces

## Github Repos

- [playing-cards](https://github.com/ddc-java-18/playing-cards-ivan-pd): A java application for a cool card trick.
  - Using the Iterable Interface

## Notes

- Primitives are passed by value. Objects are passed by reference.
- Methods sit on the stack in Stack frames
  - Each invocation of a method has its own stack frame.
- There is a unique circumstance when you have final primitives. If they are re-assigned then we cannot reset the value.
  - However, if we have a final array. we can still re-assign the the elements in the array since the array is Abject and the values inside are references. However, you cannot re-assign the actual array object.
  - Deep copy vs Shallow Copy
- The garbage collector marks memory on the heap as available for reuse. Then when a new object is added to the heap it shifts around memory to allocate enough memory for the new object. this can include
- Strategy Design Pattern
  - By using a comparator for sorting a list we are using the strategy pattern. We can pass multiple different comparators to switch up the sorting strategy.
  - If a list and its objects have a natural ordering. Then you can pass null into the `.sort`(null) method and it will use this natural ordering for the sorting.
- When you override a method that you inherit you cannot change its access modifier.
  - If you could do this then you would violate the Liskov substitution principle
- Favor composition over inheritance
- Composition = Has a “x” rather than “Is-A” “x” which would be inheritance.
- Two main implementations of Lists:
  - ArrayList: When we will be moving a lot of items around in the list (like shuffling) we want to use an ArrayList.
  - LinkedList: When we will be appending things at the start and end of the list.
- Unchecked vs Checked Exceptions
  - Unchecked: Compiler
    - Runtime Exceptions
    - Usually the result of a coding problem.
  - Check Exceptions:
    - We must catch it or must announce that we can throw this exception.
    - Non-Runtime Exceptions

## REST:

- HTTP: Hypertext transfer protocol
- 400 = Client Error
- 500 = Server Error
- 200 = Success
- HTTP Methods;
  - GET
  - POST: Add resource represented by body content to target resource collection. Or request the target resource process data provided in body.
    - the URI refers to a resource that can process the data rather than a collection.
  - PUT: Create or replace target resource with resource represented by body content.
  - PATCH: Modify target resource according to changes in provided body.
  - DELETE

## Fibonnaci Sequence Using Iterator & Iterable

```
class FibIterable implements Iterable<Long> {
	private final int length;
  public FibIterable(int length) {
	  this.length = length;
  }

  public Iterator<Long> iterator() {
	  return new FibIterator(length);
  }
}

class FibIterator implements Iterator<Long> {
	private long previous = -1;
	private long current = 1;
	private final int length;
	private int count = 0;

	public FibIterator(int length){
	 this.length = length;
	}

 @Override
 public boolean hasNext(){
	 return (count < length);
 }

 @Override
 public Long next(){
	 count += 1;
	 long next = previous + current;
	 previous = current;
	 current = next;
	 return next;
 }
}

// JShell
for (long f : new FibIterable(83)){
	System.out.println(f);
}

```
