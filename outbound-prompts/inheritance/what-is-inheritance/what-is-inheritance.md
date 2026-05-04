# Inheritance - Eval Prompts

Source: https://dev.java/learn/inheritance/what-is-inheritance/

---

## Code Block 1

**Score:** 5 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class Bicycle {
        
    // the Bicycle class has three fields
    public int cadence;
    public int gear;
    public int speed;
        
    // the Bicycle class has one constructor
    public Bicycle(int startCadence, int startSpeed, int startGear) {
        gear = startGear;
        cadence = startCadence;
        speed = startSpeed;
    }
        
    // the Bicycle class has four methods
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

public class MountainBike extends Bicycle {

    // the MountainBike subclass adds one field
    public int seatHeight;

    // the MountainBike subclass has one constructor
    public MountainBike(int startHeight,
                        int startCadence,
                        int startSpeed,
                        int startGear) {
        super(startCadence, startSpeed, startGear);
        seatHeight = startHeight;
    }

    // the MountainBike subclass adds one method
    public void setHeight(int newValue) {
        seatHeight = newValue;
    }
}
```

**Prose Rendering (for LLM consumption):**
Define a public superclass named `Bicycle` with three public integer instance fields: `cadence`, `gear`, and `speed`. Give it a public constructor that accepts `startCadence`, `startSpeed`, and `startGear` and assigns those arguments to the three fields. Add four public instance methods: `setCadence(int newValue)`, `setGear(int newValue)`, `applyBrake(int decrement)` that subtracts from `speed`, and `speedUp(int increment)` that adds to `speed`. Then define a public subclass `MountainBike` that uses `extends Bicycle`, adds a public `int seatHeight` field, and has a public constructor taking `startHeight`, `startCadence`, `startSpeed`, and `startGear`. The first statement in the subclass constructor must be `super(startCadence, startSpeed, startGear);`, followed by assigning `seatHeight = startHeight;`. Add a public `setHeight(int newValue)` mutator for the subclass-specific field.

**Suggested Assertions:**
- Contains `class MountainBike extends Bicycle`.
- The subclass constructor calls `super(startCadence, startSpeed, startGear)` as its first statement.
- `Bicycle` declares the inherited fields `cadence`, `gear`, and `speed`.
- `MountainBike` adds a distinct `seatHeight` field and a `setHeight` method.
- `Bicycle` defines both speed-mutating methods `applyBrake` and `speedUp`.

---

## Code Block 2

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
Object obj = new MountainBike();
MountainBike myBike = (MountainBike)obj;

if (obj instanceof MountainBike) {
    MountainBike myBike = (MountainBike)obj;
}
```

**Prose Rendering (for LLM consumption):**
Show inheritance-based casting with a `MountainBike` instance stored in a variable of type `Object`. First perform implicit upcasting by assigning `new MountainBike()` to an `Object` variable named `obj`. Then demonstrate explicit downcasting with `MountainBike myBike = (MountainBike)obj;`. Also include a guarded version that checks `if (obj instanceof MountainBike)` before performing the cast inside the block. The example should make clear that downcasting requires an explicit cast and that `instanceof` is used to avoid a bad runtime cast.

**Suggested Assertions:**
- Contains an `Object` variable assigned from `new MountainBike()`.
- Uses explicit downcast syntax with `(MountainBike)`.
- Includes an `instanceof MountainBike` check before a cast.
- Performs the guarded cast inside the `if` block.

---
