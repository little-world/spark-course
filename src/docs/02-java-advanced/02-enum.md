# Enum
Java's enumeration (enum) provides a convenient way to represent a group of named constants in your code. Enums increase code readability and reduce the possibility of errors by confining possible values to a predefined set.

### Basic enum Declaration
Enums are declared using the enum keyword. For example:

```java
enum Day {
  SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY;
}
```
### Using enum Values
You can use an enum value like this:

```java
Day today = Day.WEDNESDAY;
```
### Looping Through enum Values
Enumerations come with a built-in static method values() that returns an array of all enum values:

```java

for (Day d : Day.values()) {
   System.out.println(d);
}
```
### Switch Statement with enums
Enums can be efficiently used with switch statements:

```java
switch(today) {
  case SUNDAY:
    System.out.println("Rest day!");
    break;
  case MONDAY:
    System.out.println("Start of the workweek.");
    break;
// 
}
```
### Enums with Attributes and Methods
   Enums in Java are more powerful than many other languages. They can have attributes, constructors, and methods.

```java

enum Planet {
    MERCURY(3.303e+23, 2.4397e6),
    VENUS(4.869e+24, 6.0518e6),
    EARTH(5.976e+24, 6.3781e6);

    private final double mass;   // in kilograms
    private final double radius; // in meters

    Planet(double mass, double radius) {
        this.mass = mass;
        this.radius = radius;
    }

    public double getMass() {
        return mass;
    }

    public double getRadius() {
        return radius;
    }

    public double surfaceGravity() {
        return 6.67300E-11 * mass / (radius * radius);
    }
}
```

### Comparing Enums
   Enums are objects, but you can safely use == to compare their values, as there's only one object for each enum constant._

```java
if (today == Day.FRIDAY) {
  System.out.println("TGIF!");
}
```
### Best Practices
Uppercase Names: By convention, the names of enum constants are in uppercase letters.
Enums are Immutable: Once you've defined an enum constant, you can't change its value or modify its attributes.
Switch-Case: Avoid having a default case in a switch statement for enums. This way, if new values are added to the enum in the future, the compiler will alert you to handle them in the switch.


## Exercises

### Traffic Lights
Problem Statement:

Define an enum TrafficLight with values RED, YELLOW, and GREEN. Each light should have a time duration in seconds and provide a method to get this duration.

Implement a function that simulates a traffic light sequence.

Sample Output:

```text
RED: Stopped for 30 seconds.
YELLOW: Wait for 10 seconds.
GREEN: Go for 60 seconds.
```

### Pizza Order Status
Problem Statement:

Define an enum PizzaStatus with values ORDERED, PREPARING, BAKED, and DELIVERED. Each status should have a description.

Implement a method that prints the description when the status of a pizza changes.

Hint: Consider using a constructor in the enum to initialize the description.

```text
Your pizza has been ordered.
Your pizza is currently being prepared.
Your pizza has been baked.
Your pizza has been delivered.
```

### Day Type
Problem Statement:

Define an enum DayType for days of the week. The days are: MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, and SUNDAY. Classify days into WEEKDAY or WEEKEND and implement a method isWeekend() that returns whether a day is a weekend or not.

Sample Output:
```text
MONDAY is a weekday.
SUNDAY is a weekend.
```

## Solutions

### Traffic Lights
```java
enum TrafficLight {
    RED(30), YELLOW(10), GREEN(60);

    private final int duration;

    TrafficLight(int duration) {
        this.duration = duration;
    }

    public int getDuration() {
        return this.duration;
    }
}
```

```java
class Traffic {
    public void simulateTrafficLightSequence() {
        for (TrafficLight light : TrafficLight.values()) {
            switch (light) {
                case RED:
                    System.out.println("RED: Stopped for " + light.getDuration() + " seconds.");
                    break;
                case YELLOW:
                    System.out.println("YELLOW: Wait for " + light.getDuration() + " seconds.");
                    break;
                case GREEN:
                    System.out.println("GREEN: Go for " + light.getDuration() + " seconds.");
                    break;
            }
        }
    }
}
```
### Pizza Order Status
```java

enum PizzaStatus {
    ORDERED("Your pizza has been ordered."),
    PREPARING("Your pizza is currently being prepared."),
    BAKED("Your pizza has been baked."),
    DELIVERED("Your pizza has been delivered.");

    private final String description;

    PizzaStatus(String description) {
        this.description = description;
    }

    public String getDescription() {
        return this.description;
    }
    
    public void printPizzaStatus(PizzaStatus status) {
        System.out.println(status.getDescription());
    }
}
```

### Day Type
  ```java
enum DayType {
    MONDAY("weekday"), TUESDAY("weekday"), WEDNESDAY("weekday"),
    THURSDAY("weekday"), FRIDAY("weekday"), SATURDAY("weekend"), SUNDAY("weekend");

    private final String type;

    DayType(String type) {
        this.type = type;
    }

    public boolean isWeekend() {
        return this.type.equals("weekend");
   }
}
```
```java
public void printDayType(DayType day) {
    if (day.isWeekend()) {
        System.out.println(day + " is a weekend.");
    } else {
        System.out.println(day + " is a weekday.");
    }
}

```
