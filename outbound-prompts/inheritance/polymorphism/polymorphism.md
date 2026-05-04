# Polymorphism - Eval Prompts

Source: https://dev.java/learn/inheritance/polymorphism/

---

## Code Block 1

**Score:** 5 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public void printDescription(){
    IO.println("\nBike is " + "in gear " + this.gear
        + " with a cadence of " + this.cadence +
        " and travelling at a speed of " + this.speed + ". ");
}

public class MountainBike extends Bicycle {
    private String suspension;

    public MountainBike(
               int startCadence,
               int startSpeed,
               int startGear,
               String suspensionType){
        super(startCadence,
              startSpeed,
              startGear);
        this.setSuspension(suspensionType);
    }

    public String getSuspension(){
      return this.suspension;
    }

    public void setSuspension(String suspensionType) {
        this.suspension = suspensionType;
    }

    public void printDescription() {
        super.printDescription();
        IO.println("The " + "MountainBike has a" +
            getSuspension() + " suspension.");
    }
}

public class RoadBike extends Bicycle{
    // In millimeters (mm)
    private int tireWidth;

    public RoadBike(int startCadence,
                    int startSpeed,
                    int startGear,
                    int newTireWidth){
        super(startCadence,
              startSpeed,
              startGear);
        this.setTireWidth(newTireWidth);
    }

    public int getTireWidth(){
      return this.tireWidth;
    }

    public void setTireWidth(int newTireWidth){
        this.tireWidth = newTireWidth;
    }

    public void printDescription(){
        super.printDescription();
        IO.println("The RoadBike" + " has " + getTireWidth() +
            " MM tires.");
    }
}
```

**Prose Rendering (for LLM consumption):**
Start from a `Bicycle` hierarchy where instances already have inherited `gear`, `cadence`, and `speed` fields. Add an instance method `printDescription()` that prints those three values in one sentence using `IO.println`. Then define `MountainBike extends Bicycle` with a private `String suspension` field, a constructor taking cadence, speed, gear, and suspension type, and a constructor body that first calls `super(startCadence, startSpeed, startGear)` and then delegates to `setSuspension`. Provide getter and setter methods for `suspension`. Override `printDescription()` so it first calls `super.printDescription()` and then prints a second line describing the suspension. Also define `RoadBike extends Bicycle` with a private `int tireWidth`, a constructor that chains to `super`, getter/setter methods, and an overridden `printDescription()` that first calls `super.printDescription()` and then prints the tire width in millimeters.

**Suggested Assertions:**
- Both subclasses are declared with `extends Bicycle`.
- `MountainBike.printDescription()` and `RoadBike.printDescription()` each call `super.printDescription()`.
- `MountainBike` uses a `String suspension` field.
- `RoadBike` uses an `int tireWidth` field.
- Both subclass constructors call `super(startCadence, startSpeed, startGear)`.

---

## Code Block 2

**Score:** 5 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class TestBikes {
  public static void main(String[] args){
    Bicycle bike01, bike02, bike03;

    bike01 = new Bicycle(20, 10, 1);
    bike02 = new MountainBike(20, 10, 5, "Dual");
    bike03 = new RoadBike(40, 20, 8, 23);

    bike01.printDescription();
    bike02.printDescription();
    bike03.printDescription();
  }
}
```

**Prose Rendering (for LLM consumption):**
Write a `TestBikes` class with a `main` method that declares three variables of the superclass type `Bicycle`. Assign them to three different runtime objects: a plain `Bicycle`, a `MountainBike`, and a `RoadBike`. Use constructor arguments `(20, 10, 1)`, `(20, 10, 5, "Dual")`, and `(40, 20, 8, 23)` respectively. Then call `printDescription()` on each variable in order. The purpose is to demonstrate virtual method invocation: the static type of the variable remains `Bicycle`, but the JVM dispatches to the subclass override when the referenced object is a subclass instance.

**Suggested Assertions:**
- Declares multiple variables with static type `Bicycle`.
- Instantiates both `MountainBike` and `RoadBike` and stores them in `Bicycle` variables.
- Calls `printDescription()` on all three variables.
- Includes a `main(String[] args)` entry point.

---

## Code Block 3

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class Superclass {

    public void printMethod() {
        IO.println("Printed in Superclass.");
    }
}

public class Subclass extends Superclass {

    // overrides printMethod in Superclass
    public void printMethod() {
        super.printMethod();
        IO.println("Printed in Subclass");
    }
    public static void main(String[] args) {
        Subclass s = new Subclass();
        s.printMethod();
    }
}
```

**Prose Rendering (for LLM consumption):**
Define a base class `Superclass` with an instance method `printMethod()` that prints `Printed in Superclass.`. Then define `Subclass extends Superclass` and override `printMethod()`. Inside the overriding method, call `super.printMethod()` first, then print `Printed in Subclass`. Add a `main` method that constructs a `Subclass` and invokes `printMethod()`. This example should specifically exercise `super` for invoking the overridden superclass implementation from within an overriding subclass method.

**Suggested Assertions:**
- `Subclass` extends `Superclass`.
- `Subclass.printMethod()` contains a `super.printMethod()` call.
- The subclass method also prints its own message after the super call.
- `main` constructs `Subclass` and invokes `printMethod()`.

---

## Code Block 4

**Score:** 3 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
class ChessAlgorithm {
    enum ChessPlayer { WHITE, BLACK }
    ...
    final ChessPlayer getFirstPlayer() {
        return ChessPlayer.WHITE;
    }
    ...
}
```

**Prose Rendering (for LLM consumption):**
Create a class `ChessAlgorithm` containing a nested enum `ChessPlayer` with constants `WHITE` and `BLACK`. Inside the class, declare a method `getFirstPlayer()` that returns `ChessPlayer`, marks the method as `final`, and returns `ChessPlayer.WHITE`. Placeholder ellipses are acceptable around unrelated members; the key feature is a concrete `final` instance method that subclasses are not allowed to override.

**Suggested Assertions:**
- Contains a nested `enum ChessPlayer` with `WHITE` and `BLACK`.
- Declares `final ChessPlayer getFirstPlayer()`.
- The method returns `ChessPlayer.WHITE`.

---
