# Defining Methods - Eval Prompts

Source: https://dev.java/learn/classes-objects/defining-methods/

---

## Code Block 1

**Score:** 3

**Original Code:**
```java
public double calculateAnswer(double wingSpan, int numberOfEngines,
                              double length, double grossTons) {
    //do the calculation here
}
```

**Prose Rendering (for LLM consumption):**
Write an instance method declaration named `calculateAnswer` that is `public` and returns `double`. Give it four parameters in this exact order: `double wingSpan`, `int numberOfEngines`, `double length`, and `double grossTons`. Format the signature over two lines so the parameter list wraps after the second parameter. Include a method body block with a placeholder comment indicating that the calculation happens there.

**Suggested Assertions:**
- Contains a `public double calculateAnswer` method.
- Uses four parameters with types `double, int, double, double` in that order.
- Parameter names include `wingSpan`, `numberOfEngines`, `length`, and `grossTons`.
- Includes a method body delimited by braces.

---

## Code Block 2

**Score:** 5

**Original Code:**
```java
public class DataArtist {
    ...
    public void draw(String s) {
        ...
    }
    public void draw(int i) {
        ...
    }
    public void draw(double f) {
        ...
    }
    public void draw(int i, double f) {
        ...
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a public class `DataArtist` that demonstrates method overloading with four `draw` methods, all returning `void`. One overload takes a single `String s`; one takes a single `int i`; one takes a single `double f`; and one takes two parameters in order, `int i` and `double f`. Each overload should be a separate method declaration inside the same class body, showing that Java distinguishes overloads by parameter list rather than by return type.

**Suggested Assertions:**
- Contains a public class named `DataArtist`.
- Declares exactly four methods named `draw`.
- Includes overloads with parameter lists `(String)`, `(int)`, `(double)`, and `(int, double)`.
- All overloads return `void`.
- The overloaded methods appear in the same class body.

---
