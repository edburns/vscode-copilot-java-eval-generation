# Providing Constructors for your Classes - Eval Prompts

Source: https://dev.java/learn/classes-objects/defining-constructors/

---

## Code Block 1

**Score:** 4

**Original Code:**
```java
public Bicycle(int startCadence, int startSpeed, int startGear) {
    gear = startGear;
    cadence = startCadence;
    speed = startSpeed;
}
```

**Prose Rendering (for LLM consumption):**
Write a constructor for a class named `Bicycle`. The constructor must be `public`, use the class name as its identifier, and take three `int` parameters named `startCadence`, `startSpeed`, and `startGear`. Inside the body, assign `gear = startGear`, then `cadence = startCadence`, then `speed = startSpeed`. Do not declare any return type.

**Suggested Assertions:**
- Contains a constructor named `Bicycle`, not a method with a return type.
- Constructor parameter list is `(int startCadence, int startSpeed, int startGear)`.
- Constructor body assigns `gear`, `cadence`, and `speed` from the incoming parameters.
- Assignment order matches gear, cadence, speed.

---

## Code Block 2

**Score:** 4

**Original Code:**
```java
public Bicycle() {
    gear = 1;
    cadence = 10;
    speed = 0;
}
```

**Prose Rendering (for LLM consumption):**
Write an overloaded no-argument constructor for `Bicycle`. It must be `public`, have an empty parameter list, and initialize the instance fields to fixed defaults: `gear` should be set to `1`, `cadence` to `10`, and `speed` to `0`. This constructor should show how a class can provide explicit default initialization instead of relying on the compiler-generated default constructor.

**Suggested Assertions:**
- Contains a public no-argument constructor `Bicycle()`.
- Constructor assigns literal defaults to `gear`, `cadence`, and `speed`.
- Uses values `1`, `10`, and `0` respectively.
- Omits any return type.

---
