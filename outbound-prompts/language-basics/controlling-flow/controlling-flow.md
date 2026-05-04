# Control Flow Statements - Eval Prompts

Source: https://dev.java/learn/language-basics/controlling-flow/

---

## Code Block 1

**Score:** 4 (essential branching example for ordered `if` / `else if` / `else` logic)

**Original Code:**
```java
class IfElseDemo {
    public static void main(String[] args) {

        int testscore = 76;
        char grade;

        if (testscore >= 90) {
            grade = 'A';
        } else if (testscore >= 80) {
            grade = 'B';
        } else if (testscore >= 70) {
            grade = 'C';
        } else if (testscore >= 60) {
            grade = 'D';
        } else {
            grade = 'F';
        }
        IO.println("Grade = " + grade);
    }
}
```

**Prose Rendering (for LLM consumption):**
Create a class `IfElseDemo` with a `main` method. Inside it, declare `int testscore = 76;` and a `char grade;`. Use an ordered `if` / `else if` / `else` chain to assign letter grades: `A` for scores at least 90, `B` for at least 80, `C` for at least 70, `D` for at least 60, and `F` otherwise. After the conditional chain, print the result with `IO.println("Grade = " + grade);`.

**Suggested Assertions:**
- Defines `testscore` as `76`
- Declares `char grade`
- Uses a descending `if` / `else if` chain with thresholds 90, 80, 70, and 60
- Prints `"Grade = " + grade` after the conditional logic

---

## Code Block 2

**Score:** 4 (fundamental counted-loop example that every Java basics suite should exercise)

**Original Code:**
```java
class ForDemo {
    public static void main(String[] args){
         for(int i = 1; i < 11; i++){
              IO.println("Count is: " + i);
         }
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a class `ForDemo` with a `main` method containing a classic counted `for` loop. The loop variable should be `int i = 1`, the termination condition should be `i < 11`, and the increment expression should be `i++`. Inside the loop body, print `"Count is: " + i` on each iteration so the program emits the numbers 1 through 10.

**Suggested Assertions:**
- Uses a `for` loop with initialization, termination, and increment expressions
- Initializes `i` to `1`
- Uses the condition `i < 11`
- Prints `"Count is: " + i` inside the loop

---

## Code Block 3

**Score:** 5 (high-value labeled-break example with nested loops and 2D-array search)

**Original Code:**
```java
class BreakWithLabelDemo {
    public static void main(String[] args) {

        int[][] arrayOfInts = {
            {  32,   87,    3, 589 },
            {  12, 1076, 2000,   8 },
            { 622,  127,   77, 955 }
        };
        int searchfor = 12;

        int i;
        int j = 0;
        boolean foundIt = false;

    search:
        for (i = 0; i < arrayOfInts.length; i++) {
            for (j = 0; j < arrayOfInts[i].length;
                 j++) {
                if (arrayOfInts[i][j] == searchfor) {
                    foundIt = true;
                    break search;
                }
            }
        }

        if (foundIt) {
            IO.println("Found " + searchfor + " at " + i + ", " + j);
        } else {
            IO.println(searchfor + " not in the array");
        }
    }
}
```

**Prose Rendering (for LLM consumption):**
Create a class `BreakWithLabelDemo` with a `main` method that searches a two-dimensional `int` array for the value `12`. Initialize `arrayOfInts` as a 3x4 literal matrix, set `searchfor` to `12`, and declare index variables `i`, `j`, plus a boolean `foundIt = false`. Place a label named `search` before the outer `for` loop. Inside nested loops over rows and columns, compare `arrayOfInts[i][j]` to `searchfor`; when they match, set `foundIt = true` and exit both loops with `break search;`. After the loops, print either the found coordinates or a not-found message.

**Suggested Assertions:**
- Declares a two-dimensional `int[][]` literal
- Uses nested `for` loops with a label named `search`
- Breaks out of the outer loop with `break search;`
- Prints the found coordinates using both `i` and `j`

---

## Code Block 4

**Score:** 5 (excellent labeled-continue example with nested-loop substring search)

**Original Code:**
```java
class ContinueWithLabelDemo {
    public static void main(String[] args) {

        String searchMe = "Look for a substring in me";
        String substring = "sub";
        boolean foundIt = false;

        int max = searchMe.length() -
                  substring.length();

    test:
        for (int i = 0; i <= max; i++) {
            int n = substring.length();
            int j = i;
            int k = 0;
            while (n-- != 0) {
                if (searchMe.charAt(j++) != substring.charAt(k++)) {
                    continue test;
                }
            }
            foundIt = true;
                break test;
        }
        IO.println(foundIt ? "Found it" : "Didn't find it");
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a class `ContinueWithLabelDemo` whose `main` method searches for the substring `"sub"` inside the string `"Look for a substring in me"`. Compute `max` as the largest valid starting index, then place a label `test` on the outer `for` loop that advances possible starting positions. Inside that loop, initialize counters `n`, `j`, and `k`, and use a `while (n-- != 0)` loop to compare characters from the larger string and the substring. If any character pair differs, skip immediately to the next outer-loop iteration with `continue test;`. If the whole substring matches, set `foundIt = true`, break out with `break test;`, and finally print either `"Found it"` or `"Didn't find it"` with a ternary expression.

**Suggested Assertions:**
- Defines `searchMe` and `substring` string variables
- Computes `max` from the difference in string lengths
- Uses a label named `test` with `continue test;`
- Uses a nested `while (n-- != 0)` character-comparison loop

---

## Code Block 5

**Score:** 4 (important modern control-flow example using `yield` inside a switch expression)

**Original Code:**
```java
class Test {
    enum Day {
        MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY
    }

    public int calculate(Day d) {
        return switch (d) {
            case SATURDAY, SUNDAY -> 0;
                default -> {
                    int remainingWorkDays = 5 - d.ordinal();
                    yield remainingWorkDays;
                }
            };
    }
}
```

**Prose Rendering (for LLM consumption):**
Create a class `Test` containing an inner `enum Day` with all seven weekdays. Add a method `calculate` that takes a `Day d` and returns an `int` by directly returning a `switch` expression on `d`. For `SATURDAY` and `SUNDAY`, use arrow syntax and return `0`. In the `default` arm, use a block, declare a local variable `remainingWorkDays = 5 - d.ordinal();`, and return that value with `yield remainingWorkDays;`.

**Suggested Assertions:**
- Declares an inner enum `Day` with all seven constants
- Returns a `switch (d)` expression directly from the method
- Uses a multi-label arrow case for `SATURDAY, SUNDAY -> 0`
- Uses `yield` inside a block in the `default` case
