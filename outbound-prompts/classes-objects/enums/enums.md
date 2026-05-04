# Enums - Eval Prompts

Source: https://dev.java/learn/classes-objects/enums/

---

## Code Block 1

**Score:** 5

**Original Code:**
```java
DayOfWeek someDay = DayOfWeek.FRIDAY;

String text = switch (someDay) {
    case MONDAY -> "The week just started.";
    case TUESDAY, WEDNESDAY, THURSDAY -> "We are somewhere in the middle of the week.";
    case FRIDAY -> "The weekend is near.";
    case SATURDAY, SUNDAY -> "Weekend";
};

IO.println(text);
```

**Prose Rendering (for LLM consumption):**
Write a snippet that assigns `DayOfWeek.FRIDAY` to a variable `someDay`, then uses a switch expression to compute a `String text`. The switch expression must cover all seven enum constants with arrow labels, grouping `TUESDAY, WEDNESDAY, THURSDAY` together and `SATURDAY, SUNDAY` together. Return distinct string literals for Monday, midweek, Friday, and weekend, then print the result with `IO.println(text)`. Do not include a `default` arm so the code relies on enum exhaustiveness.

**Suggested Assertions:**
- Uses a switch expression, not a traditional switch statement.
- Switch target is a `DayOfWeek` enum variable.
- Groups multiple enum constants in at least two case labels.
- Omits a `default` branch.
- Assigns the switch result to a `String` variable named `text`.

---

## Code Block 2

**Score:** 5

**Original Code:**
```java
public enum DayOfWeek {
    MONDAY("MON"), TUESDAY("TUE"), WEDNESDAY("WED"), THURSDAY("THU"), FRIDAY("FRI"), SATURDAY("SAT"), SUNDAY("SUN");    

    private final String abbreviation;

    DayOfWeek(String abbreviation) {
        this.abbreviation = abbreviation;
    }

    public String getAbbreviation() {
        return abbreviation;
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a public enum `DayOfWeek` whose constants each carry a three-letter abbreviation string: `MONDAY("MON")`, `TUESDAY("TUE")`, `WEDNESDAY("WED")`, `THURSDAY("THU")`, `FRIDAY("FRI")`, `SATURDAY("SAT")`, and `SUNDAY("SUN")`. Terminate the constant list with a semicolon, then declare a private final field `abbreviation`. Add an enum constructor `DayOfWeek(String abbreviation)` that stores the value with `this.abbreviation = abbreviation`, and expose a public getter `getAbbreviation()` returning the field.

**Suggested Assertions:**
- Declares `public enum DayOfWeek`.
- Enum constants pass constructor arguments in parentheses.
- Includes a semicolon after the constant list.
- Declares `private final String abbreviation`.
- Includes an enum constructor and a `getAbbreviation()` method.

---

## Code Block 3

**Score:** 5

**Original Code:**
```java
enum MyEnum {
    A() {
        @Override
        void doSomething() {
            IO.println("a");
        }
    },
    B() {
        @Override
        void doSomething() {
            IO.println("b");
        }
    };

    abstract void doSomething();
}
```

**Prose Rendering (for LLM consumption):**
Write an enum `MyEnum` with two constants, `A` and `B`, where each constant has its own class body overriding an abstract method. For constant `A`, override `doSomething()` to print `"a"` with `IO.println`; for constant `B`, override `doSomething()` to print `"b"`. After the constant declarations, place a semicolon and declare `abstract void doSomething();` at enum scope so every constant must implement it.

**Suggested Assertions:**
- Declares an enum named `MyEnum`.
- Each enum constant has its own class body.
- Both constants annotate the override with `@Override`.
- Declares `abstract void doSomething();` after the constant list.
- Constant-specific implementations print different string literals.

---
