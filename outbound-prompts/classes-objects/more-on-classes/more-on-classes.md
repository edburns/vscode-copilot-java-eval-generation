# More on Classes - Eval Prompts

Source: https://dev.java/learn/classes-objects/more-on-classes/

---

## Code Block 1

**Score:** 4

**Original Code:**
```java
public class Point {
    public int x = 0;
    public int y = 0;

    //constructor
    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a public `Point` class with public integer fields `x` and `y`, each initialized to `0`. Add a constructor `Point(int x, int y)` where the parameter names intentionally shadow the field names. Use the `this` keyword on both assignments so the constructor body reads `this.x = x;` and `this.y = y;`.

**Suggested Assertions:**
- Contains a public class named `Point`.
- Declares fields `x` and `y` initialized to `0`.
- Constructor parameters are also named `x` and `y`.
- Uses `this.x = x` and `this.y = y`.

---

## Code Block 2

**Score:** 5

**Original Code:**
```java
public class Rectangle {
    private int x, y;
    private int width, height;

    public Rectangle() {
        this(0, 0, 1, 1);
    }
    public Rectangle(int width, int height) {
        this(0, 0, width, height);
    }
    public Rectangle(int x, int y, int width, int height) {
        this.x = x;
        this.y = y;
        this.width = width;
        this.height = height;
    }
    ...
}
```

**Prose Rendering (for LLM consumption):**
Write a public `Rectangle` class with four private integer fields: `x`, `y`, `width`, and `height`. Implement constructor chaining with `this(...)`: a no-argument constructor delegates to `this(0, 0, 1, 1)`, and a two-argument constructor `Rectangle(int width, int height)` delegates to `this(0, 0, width, height)`. The canonical four-argument constructor `Rectangle(int x, int y, int width, int height)` assigns all four fields using `this.x`, `this.y`, `this.width`, and `this.height`.

**Suggested Assertions:**
- Declares private fields `x`, `y`, `width`, and `height`.
- No-arg constructor calls `this(0, 0, 1, 1)`.
- Two-arg constructor calls `this(0, 0, width, height)`.
- Four-arg constructor assigns all fields using the `this` qualifier.

---

## Code Block 3

**Score:** 5

**Original Code:**
```java
public class Bicycle {

    private int cadence;
    private int gear;
    private int speed;

    private int id;

    private static int numberOfBicycles = 0;


    public Bicycle(int startCadence,
                   int startSpeed,
                   int startGear) {
        gear = startGear;
        cadence = startCadence;
        speed = startSpeed;

        id = ++numberOfBicycles;
    }

    public int getID() {
        return id;
    }

    public static int getNumberOfBicycles() {
        return numberOfBicycles;
    }

    public int getCadence() {
        return cadence;
    }

    public void setCadence(int newValue) {
        cadence = newValue;
    }

    public int getGear(){
        return gear;
    }

    public void setGear(int newValue) {
        gear = newValue;
    }

    public int getSpeed() {
        return speed;
    }

    public void applyBrake(int decrement) {
        speed -= decrement;
    }

    public void speedUp(int increment) {
        speed += increment;
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a public `Bicycle` class combining instance state and class state. Declare private instance fields `cadence`, `gear`, `speed`, and `id`, plus a private static field `numberOfBicycles` initialized to `0`. The constructor `Bicycle(int startCadence, int startSpeed, int startGear)` should assign the three motion-related fields and then set `id = ++numberOfBicycles` so each instance gets a unique identifier while incrementing the shared class counter. Add an instance getter `getID()`, a static getter `getNumberOfBicycles()`, instance getters and setters for cadence and gear, an instance getter for speed, and behavior methods `applyBrake(int decrement)` and `speedUp(int increment)` that mutate `speed`.

**Suggested Assertions:**
- Declares a private static field `numberOfBicycles` initialized to `0`.
- Constructor increments the static counter with pre-increment and assigns the result to `id`.
- Includes a static method `getNumberOfBicycles()`.
- Includes an instance method `getID()`.
- Separates static class state from per-instance fields.

---
