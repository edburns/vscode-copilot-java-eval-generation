# Creating Classes - Eval Prompts

Source: https://dev.java/learn/classes-objects/creating-classes/

---

## Code Block 1

**Score:** 5

**Original Code:**
```java
public class Bicycle {
        
    // the Bicycle class has
    // three fields
    public int cadence;
    public int gear;
    public int speed;
        
    // the Bicycle class has
    // one constructor
    public Bicycle(int startCadence, int startSpeed, int startGear) {
        gear = startGear;
        cadence = startCadence;
        speed = startSpeed;
    }
        
    // the Bicycle class has
    // four methods
    public void setCadence(int newValue) {
        cadence = newValue;
    }
        
    public void setGear(int newValue) {
        gear = newValue;
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
Write a public class named `Bicycle` with three public `int` instance fields: `cadence`, `gear`, and `speed`. Add a three-argument public constructor taking `startCadence`, `startSpeed`, and `startGear`, and assign those parameters directly into the corresponding fields, with `gear` set first, then `cadence`, then `speed`. Define four public `void` instance methods: `setCadence(int newValue)` and `setGear(int newValue)` assign the incoming value to the matching field; `applyBrake(int decrement)` subtracts from `speed` with `-=`; and `speedUp(int increment)` adds to `speed` with `+=`.

**Suggested Assertions:**
- Contains a public class named `Bicycle`.
- Declares public `int` fields `cadence`, `gear`, and `speed`.
- Includes a constructor `Bicycle(int startCadence, int startSpeed, int startGear)`.
- Includes `applyBrake(int decrement)` using `speed -= decrement`.
- Includes `speedUp(int increment)` using `speed += increment`.

---

## Code Block 2

**Score:** 4

**Original Code:**
```java
public class MountainBike extends Bicycle {
        
    // the MountainBike subclass has
    // one field
    public int seatHeight;    // the MountainBike subclass has
    // one constructor
    public MountainBike(int startHeight, int startCadence,
                        int startSpeed, int startGear) {
        super(startCadence, startSpeed, startGear);
        seatHeight = startHeight;
    }   

    // the MountainBike subclass has
    // one method
    public void setHeight(int newValue) {
        seatHeight = newValue;
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a public subclass `MountainBike` that extends `Bicycle`. Give it one additional public `int` field named `seatHeight`. Add a public constructor with four parameters: `startHeight`, `startCadence`, `startSpeed`, and `startGear`. The constructor must call `super(startCadence, startSpeed, startGear)` first, then assign `seatHeight = startHeight`. Also define a public `void setHeight(int newValue)` method that updates the `seatHeight` field.

**Suggested Assertions:**
- Contains `class MountainBike extends Bicycle`.
- Declares a public `int seatHeight` field.
- Constructor has four parameters and calls `super(startCadence, startSpeed, startGear)`.
- Constructor assigns `seatHeight = startHeight`.
- Includes `setHeight(int newValue)` that writes to `seatHeight`.

---

## Code Block 3

**Score:** 5

**Original Code:**
```java
public class Bicycle {

    private int cadence;
    private int gear;
    private int speed;

    public Bicycle(int startCadence, int startSpeed, int startGear) {
        gear = startGear;
        cadence = startCadence;
        speed = startSpeed;
    }

    public int getCadence() {
        return cadence;
    }

    public void setCadence(int newValue) {
        cadence = newValue;
    }

    public int getGear() {
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
Write a public `Bicycle` class that demonstrates encapsulation by making the state fields private. Declare private `int` fields named `cadence`, `gear`, and `speed`. Provide a public constructor `Bicycle(int startCadence, int startSpeed, int startGear)` that assigns those incoming values into the three fields. Add public getter methods `getCadence()`, `getGear()`, and `getSpeed()` that each return the corresponding field. Add public setter methods `setCadence(int newValue)` and `setGear(int newValue)` that assign the provided value. Keep behavior methods `applyBrake(int decrement)` and `speedUp(int increment)` as public `void` methods that mutate `speed` with compound assignment.

**Suggested Assertions:**
- Declares private `int` fields `cadence`, `gear`, and `speed`.
- Exposes public getters `getCadence`, `getGear`, and `getSpeed` returning `int`.
- Exposes public setters for cadence and gear.
- Does not declare `speed` as public.
- Includes behavior methods that mutate `speed` rather than a public speed setter.

---
