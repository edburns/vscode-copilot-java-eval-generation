# Abstract Methods and Classes - Eval Prompts

Source: https://dev.java/learn/inheritance/abstract-classes/

---

## Code Block 1

**Score:** 5 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
abstract class GraphicObject {
    int x, y;
    ...
    void moveTo(int newX, int newY) {
        ...
    }
    abstract void draw();
    abstract void resize();
}
```

**Prose Rendering (for LLM consumption):**
Define an abstract class named `GraphicObject`. It should contain concrete state fields `int x, y`, a concrete instance method `moveTo(int newX, int newY)` for shared movement behavior, and two abstract instance methods `draw()` and `resize()` declared without method bodies. Placeholder ellipses are acceptable for omitted implementation details, but the structure must clearly mix shared concrete behavior with required abstract behavior in the same abstract superclass.

**Suggested Assertions:**
- Declares `abstract class GraphicObject`.
- Contains concrete fields such as `int x, y`.
- Includes a concrete `moveTo(int newX, int newY)` method.
- Declares both `abstract void draw()` and `abstract void resize()`.

---

## Code Block 2

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
class Circle extends GraphicObject {
    void draw() {
        ...
    }
    void resize() {
        ...
    }
}
class Rectangle extends GraphicObject {
    void draw() {
        ...
    }
    void resize() {
        ...
    }
}
```

**Prose Rendering (for LLM consumption):**
Implement two concrete subclasses, `Circle` and `Rectangle`, both extending `GraphicObject`. Each subclass must provide concrete implementations of the inherited abstract methods `draw()` and `resize()`. The method bodies can be placeholders, but both subclasses should be non-abstract and visibly satisfy the abstract contract imposed by `GraphicObject`.

**Suggested Assertions:**
- Contains both `class Circle extends GraphicObject` and `class Rectangle extends GraphicObject`.
- Each subclass implements `draw()`.
- Each subclass implements `resize()`.
- Neither subclass is declared `abstract`.

---

## Code Block 3

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
abstract class X implements Y {
  // implements all but one method of Y
}

class XX extends X {
  // implements the remaining method in Y
}
```

**Prose Rendering (for LLM consumption):**
Show partial interface implementation through an abstract class. Define an abstract class `X` that `implements Y` but intentionally leaves at least one interface method unimplemented, which is why `X` itself must remain abstract. Then define a concrete subclass `XX extends X` that supplies the remaining missing interface method. The exact interface members can stay schematic; the important language feature is that an abstract class may implement an interface without completing every method, while a concrete subclass finishes the contract.

**Suggested Assertions:**
- Declares `abstract class X implements Y`.
- Declares `class XX extends X`.
- Preserves the idea that `X` is abstract because it does not implement all of `Y`.
- Shows `XX` as the concrete class that completes the interface contract.

---
