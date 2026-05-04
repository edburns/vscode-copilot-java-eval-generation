# Branching with Switch Expressions - Eval Prompts

Source: https://dev.java/learn/language-basics/switch-expression/

---

## Code Block 1

**Score:** 5 (one of the clearest possible evals for arrow-style switch-expression syntax)

**Original Code:**
```java
Day day = ...; // any day
int len =
    switch (day) {
        case MONDAY, FRIDAY, SUNDAY -> 6;
        case TUESDAY                -> 7;
        case THURSDAY, SATURDAY     -> 8;
        case WEDNESDAY              -> 9;
    };
IO.println("len = " + len);
```

**Prose Rendering (for LLM consumption):**
Write a snippet that declares a `Day` variable named `day` and computes an integer `len` with a `switch` expression rather than a traditional switch statement. Use arrow-style labels and assign the result of the entire `switch` expression directly to `len`. Group `MONDAY`, `FRIDAY`, and `SUNDAY` in one comma-separated case that yields `6`; use separate cases for `TUESDAY` yielding `7`, `THURSDAY` and `SATURDAY` yielding `8`, and `WEDNESDAY` yielding `9`. After the switch expression, print `"len = " + len`.

**Suggested Assertions:**
- Assigns the result of a `switch (day)` expression directly to `len`
- Uses arrow syntax `case ... ->`
- Includes at least one comma-separated multi-label case
- Prints the computed `len` after the switch expression

---

## Code Block 2

**Score:** 4 (good direct-value example showing that switch expressions can replace assignment scaffolding)

**Original Code:**
```java
int quarter = ...; // any value

String quarterLabel =
    switch (quarter) {
        case 0  -> "Q1 - Winter";
        case 1  -> "Q2 - Spring";
        case 2  -> "Q3 - Summer";
        case 3  -> "Q3 - Summer";
        default -> "Unknown quarter";
    };
```

**Prose Rendering (for LLM consumption):**
Create a switch expression over an integer `quarter` that directly produces a `String` assigned to `quarterLabel`. Use arrow cases for `0`, `1`, `2`, and `3`, returning the quarter labels `"Q1 - Winter"`, `"Q2 - Spring"`, `"Q3 - Summer"`, and again `"Q3 - Summer"`. Include a `default` arm that returns `"Unknown quarter"`. The value should come from the switch expression itself, not from assignments inside a traditional switch block.

**Suggested Assertions:**
- Declares `String quarterLabel = switch (quarter) { ... };`
- Uses arrow cases for numeric constants `0` through `3`
- Includes a `default -> "Unknown quarter"`
- Produces values directly from the switch arms rather than mutating a variable inside cases

---

## Code Block 3

**Score:** 5 (essential `yield` example for block-bodied switch-expression arms)

**Original Code:**
```java
public String convertToLabel(int quarter) {
    String quarterLabel =
        switch (quarter) {
            case 0  -> {
                IO.println("Q1 - Winter");
                yield "Q1 - Winter";
            }
            default -> "Unknown quarter";
        };
    }
    return quarterLabel;
}
```

**Prose Rendering (for LLM consumption):**
Write a method `convertToLabel` that takes `int quarter` and returns `String`. Inside the method, declare `String quarterLabel` and assign it from a `switch (quarter)` expression. The `case 0` arm must use arrow syntax with a block body: print `"Q1 - Winter"` inside the block and then use `yield "Q1 - Winter";` to provide the switch expression's value. Add a `default` arrow arm that evaluates to `"Unknown quarter"`, and finally return `quarterLabel`.

**Suggested Assertions:**
- Defines a method `convertToLabel(int quarter)` returning `String`
- Uses a block-bodied arrow case for `case 0`
- Calls `IO.println("Q1 - Winter")` before yielding
- Uses `yield "Q1 - Winter";` inside the switch-expression block

---

## Code Block 4

**Score:** 3 (useful compatibility example for colon-style cases inside a switch expression)

**Original Code:**
```java
int quarter = ...; // any value

String quarterLabel =
    switch (quarter) {
        case 0 :  yield "Q1 - Winter";
        case 1 :  yield "Q2 - Spring";
        case 2 :  yield "Q3 - Summer";
        case 3 :  yield "Q3 - Summer";
        default: IO.println("Unknown quarter");
                 yield "Unknown quarter";
    };
```

**Prose Rendering (for LLM consumption):**
Create a `switch` expression over `quarter` that uses traditional colon-style case labels instead of arrow labels. In each case, use the `yield` statement to produce the value of the expression: `"Q1 - Winter"`, `"Q2 - Spring"`, `"Q3 - Summer"`, and `"Q3 - Summer"` for cases 0 through 3. In the `default` branch, first print `"Unknown quarter"` and then `yield "Unknown quarter";`.

**Suggested Assertions:**
- Uses a `switch` expression with colon-style `case` labels
- Uses `yield` in every branch rather than `break`
- Includes a `default` branch that prints before yielding
- Assigns the switch expression result to `quarterLabel`
