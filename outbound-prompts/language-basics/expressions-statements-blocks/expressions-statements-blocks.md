# Expressions, Statements and Blocks - Eval Prompts

Source: https://dev.java/learn/language-basics/expressions-statements-blocks/

---

## Code Block 1

**Score:** 3 (small but useful operator-precedence eval for expressions)

**Original Code:**
```java
x + y / 100   // ambiguous

x + (y / 100) // unambiguous, recommended
```

**Prose Rendering (for LLM consumption):**
Provide a tiny expression-focused snippet that contrasts implicit operator precedence with explicit parentheses. The first line should be the arithmetic expression `x + y / 100` followed by a comment noting that it is ambiguous to readers. After a blank line, show the version `x + (y / 100)` with a comment saying it is unambiguous and recommended. The goal is to demonstrate that division binds more tightly than addition and that parentheses improve readability.

**Suggested Assertions:**
- Contains the expression `x + y / 100`
- Contains a second version with explicit parentheses around `y / 100`
- Includes comments calling out ambiguity vs. the recommended form
- Shows the two versions as separate lines in the same snippet

---

## Code Block 2

**Score:** 4 (canonical floating-point precision gotcha that belongs in Java basics evals)

**Original Code:**
```java
double d1 = 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1;
IO.println("d1 == 1 ? " + (d1 == 1.0));
```

**Prose Rendering (for LLM consumption):**
Write a two-line snippet demonstrating floating-point precision surprises. First, declare a `double` variable named `d1` and initialize it by adding the literal `0.1` ten times in a single expression. On the next line, print a message that starts with `"d1 == 1 ? "` and concatenates the boolean result of the equality check `(d1 == 1.0)`. The point is that the comparison looks like it should be true but is not guaranteed to be.

**Suggested Assertions:**
- Declares `double d1`
- Builds `d1` from repeated `0.1` additions instead of assigning `1.0` directly
- Compares `d1` to `1.0` with `==`
- Prints the comparison result with a descriptive prefix string

---

## Code Block 3

**Score:** 3 (good brace/block-structure example around if/else control flow)

**Original Code:**
```java
class BlockDemo {
     public static void main(String[] args) {
          boolean condition = true;
          if (condition) { // begin block 1
               IO.println("Condition is true.");
          } // end block one
          else { // begin block 2
               IO.println("Condition is false.");
          } // end block 2
     }
}
```

**Prose Rendering (for LLM consumption):**
Create a class `BlockDemo` with a `main` method. Inside `main`, declare a boolean variable `condition` initialized to `true`. Then write an `if/else` statement using explicit braces for both branches. In the true branch, print `"Condition is true."`; in the false branch, print `"Condition is false."`. Preserve the instructional comments that mark the start and end of each block so the snippet clearly emphasizes balanced braces and block structure.

**Suggested Assertions:**
- Defines class `BlockDemo` with `main(String[] args)`
- Declares `boolean condition = true`
- Uses both `if (condition) { ... }` and `else { ... }`
- Includes comments identifying block boundaries
