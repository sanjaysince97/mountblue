# Design patterns in JAVA

A design pattern is a proved solution for any problem.

There are specifications and a set of rules in every pattern for solving problems. Design patterns are categorised based on these specifications.

#### Advantages of Design patterns:

- we can use design patterns in multiple projects
- Helps to define system architecture of the project
- Application design is transparent.
- Created by software professionals and experts so its proved and tested solution.
- It provides clarity for building a better system and system architecture.
- It also provides prior hands-on experience.

#### Limitations of Design patter:

We can't have a design pattern for every problem we face in software development. So whenever we find a problem without any design pattern, after solving the problem we should make proper documentation.

In Software Development Life Cycle design pattern must use in the initial stage like Analysis and requirement phase. Using design pattern in this phase makes the job easy.

## Categories

1. Core Java Design Patterns.
2. JEE Design Patterns.

### Core Java Design Patterns

There are three types of design patterns in core java, and they are further divided into 23 sub-parts.

##### 1. Creational Design Pattern

 As its name, it focuses on the creation of objects and classes

1. Factory Pattern

2. Abstract Factory Pattern

3. Singleton Pattern

   In this design pattern a class is restricted to initialise one "single" instance. 

   ```java
   public class MySingleton {
   	// initialization
   	private static MySingleton instance = null;
   
   	// private constructor to prevent object instantialization outside this class.
   	private MySingleton(){
           
       }
   
   	// check if the instance is null, within a synchronized block. If so, create the object
   	public static MySingleton getInstance(){
   		synchronized (MySingleton.class) {
   			if (instance == null) {
   				instance = new MySingleton();
   			}
   		}
   		return instance;
   	}
   }
   ```

   

4. Prototype Pattern

5. Builder Pattern.

   In this type of pattern object is created in multiple way based on the given options.

   ```java
   public class BuilderPattern {
       static class Coffee {
   		private Coffee(Builder builder) {
               this.type = builder.type;
               this.sugar = builder.sugar;
               this.milk = builder.milk;
               this.size = builder.size;
           }
           private String type;
           private boolean sugar;
           private boolean milk;
           private String size;
           public static class Builder {
               private String type;
               private boolean sugar;
               private boolean milk;
               private String size;
               public Builder(String type) {
                   this.type = type;
               }
               public Builder sugar(boolean value) {
                   this.sugar = value;
                   return this;
               }
               public Builder milk(boolean value) {
                   this.milk = value;
                   return this;
               }
               public Builder size(String value) {
                   this.size = value;
                   return this;
               }
               public Coffee build() {
                   return new Coffee(this);
               }
           }
           public String toString() {
               return String.format("Coffee [type=%s, sugar=%s, milk=%s, size=%s]", this.type, sugar, milk, size);
           }
       }
       public static void main(String[] args) {
           Coffee coffee = new BuilderPattern.Coffee.Builder("Mocha").milk(true).sugar(false).size("Large").build();
           System.out.println(coffee);
       }
   }
   ```

   

##### 2. Structural Design Pattern

 It focuses on the structure of objects and classes which helps in identifying relationships between them.

1. Adapter Pattern
2. Bridge Pattern
3. Composite Pattern
4. Decorator Pattern
5. Facade Pattern
6. Flyweight Pattern
7. Proxy Pattern

##### 3. Behavioural Design Pattern

 It focuses on responsibility and interaction on the objects, and also focuses on coupling and dependencies.

1. Chain Of Responsibility Pattern

2. Command Pattern

3. Interpreter Pattern

4. Iterator Pattern

5. Mediator Pattern

6. Memento Pattern

7. Observer Pattern

   In this pattern we notify a change to numbers of classes.

   ```java
   public class Observer Pattern {
           static class SachinCenturyNotifier {
               List<SachinFan> fans = new ArrayList<SachinFan>();
               void register(SachinFan fan) {
                   fans.add(fan);
               }
               void sachinScoredACentury() {
                   for(SachinFan fan: fans) {
                       fan.announce();
                   }
               }
           }
           static class SachinFan {
               private String name;
               SachinFan(String name) {
                   this.name = name;
               }
               void announce() {
                   System.out.println(name + " notified");
               }
           }
           public static void main(String[] args) {
               SachinCenturyNotifier notifier = new SachinCenturyNotifier();
               notifier.register(new SachinFan("Ranga"));
               notifier.register(new SachinFan("Ramya"));
               notifier.register(new SachinFan("Veena"));
               notifier.sachinScoredACentury();
           }
       }
   ```

   

8. State Pattern

   This pattern is used in which we have different states of object. In below example fan is an object which has many speed levels. 

   ```java
   public class StatePattern {
           static class FanWallControl {
               private SpeedLevel current;
               public FanWallControl() {
                   current = new Off();
               }
               public void set_state(SpeedLevel state) {
                   current = state;
               }
               public void rotate() {
                   current.rotate(this);
               }
   
               public String toString() {
                   return String.format("Fan Wall Control [current = %s]", current);
               }
           }
           interface speedLevel {
               void rotate(FanWallControl fanWallControl);
           }
           static class Off implements SpeedLevel {
               public void rotate(FanWallControl fanWallControl) {
                   fanWallControl.set_state(new SpeedLevel1());
               }
           }
           static class SpeedLevel1 implements SpeedLevel {
               public void rotate(FanWallControl fanWallControl) {
                   fanWallControl.set_state(new SpeedLevel2());
               }
           }
           static class SpeedLevel2 implements SpeedLevel {
               public void rotate(FanWallControl fanWallControl) {
                   fanWallControl.set_state(new SpeedLevel3());
               }
           }
           static class SpeedLevel3 implements SpeedLevel {
               public void rotate(FanWallControl fanWallControl) {
                   fanWallControl.set_state(new Off());
               }
           }
       }
   ```

   

9. Strategy Pattern

   In Strategy we encapsulate an algorithm inside a class.

   ```java
   public class StrategyPattern {
           interface Sortable {
               public int[] sort(int[] numbers);
           }
           static class BubbleSort implements Sortable {
               @Override
               public int[] sort(int[] numbers) {
                   //sort using bubble sort algorithm
                   return numbers;
               }
           }
           static class QuickSort implements Sortable {
               @Override
               public int[] sort(int[] numbers) {d
                   //sort using quicksort algorithm
                   return numbers;
               }
           }
           static class ComplexClass {
               private Sortable sorter;
               ComplexClass(Sortable sorter) {
                   this.sorter = sorter;
               }
               void doAComplexThing() {
                   int[] values = null;
                   //logic...
                   sorter.sort(values);
                   //logic...
               }
           }
           public static void main(String[] args) {
               ComplexClass complexClassInstance = new ComplexClass(new BubbleSort());
               complexClassInstance.doAComplexThing();
           }
       }
   ```

   

10. Template Pattern

11. Visitor Pattern

    

    
