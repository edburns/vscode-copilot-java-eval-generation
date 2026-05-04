# Records - Eval Prompts

Source: https://dev.java/learn/records/

---

## Code Block 1

**Score:** 5 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
record Point(int x, int y) {}
```

**Prose Rendering (for LLM consumption):**
Declare a top-level Java record named `Point` with exactly two components, `x` and `y`, both of type `int`. Use record syntax rather than a class, and leave the body empty so the compiler supplies the canonical constructor, accessors `x()` and `y()`, plus `equals()`, `hashCode()`, and `toString()`.

**Suggested Assertions:**
- Declares a `record` named `Point`.
- The record header contains exactly `int x, int y` in that order.
- Uses record syntax, not `class` syntax.
- Does not declare setters or mutable instance fields.

---

## Code Block 2

**Score:** 5 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
record Range(int start, int end) {
    public Range {
        if (end <= start) {
            throw new IllegalArgumentException("End must be greater than start");
        }
    }
}
```

**Prose Rendering (for LLM consumption):**
Declare a record named `Range` with two `int` components named `start` and `end`. Override the canonical constructor using the compact-constructor form `public Range { ... }` with no explicit parameter list. Inside that compact constructor, validate the component values and throw an `IllegalArgumentException` when `end` is less than or equal to `start`. Do not assign to the fields directly; rely on record constructor semantics.

**Suggested Assertions:**
- Declares `record Range(int start, int end)`.
- Includes a compact constructor `public Range {` rather than a constructor with an explicit parameter list.
- Throws `IllegalArgumentException` when `end <= start`.
- Does not assign to `this.start` or `this.end` inside the compact constructor.

---

## Code Block 3

**Score:** 5 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
import java.util.List;

record State(String name, String capitalCity, List<String> cities) {
    public State {
        cities = List.copyOf(cities);
    }

    public State(String name, String capitalCity) {
        this(name, capitalCity, List.of());
    }

    public State(String name, String capitalCity, String... cities) {
        this(name, capitalCity, List.of(cities));
    }

    @Override
    public List<String> cities() {
        return List.copyOf(cities);
    }
}
```

**Prose Rendering (for LLM consumption):**
Create a record named `State` with three components: `String name`, `String capitalCity`, and `List<String> cities`. In the compact canonical constructor, replace the incoming `cities` reference with `List.copyOf(cities)` so the record stores an unmodifiable defensive copy. Add one overloaded constructor that accepts only `name` and `capitalCity` and delegates to the canonical constructor with `List.of()`. Add another overloaded constructor that accepts a varargs `String... cities` parameter and delegates with `List.of(cities)`. Override the generated accessor for `cities()` so it returns a defensive copy instead of exposing the internal list reference directly.

**Suggested Assertions:**
- Declares a record `State` with components `String name`, `String capitalCity`, and `List<String> cities`.
- Uses `List.copyOf(cities)` in the compact constructor.
- Includes a two-argument constructor delegating with `this(name, capitalCity, List.of())`.
- Includes a varargs constructor `String... cities` delegating with `this(name, capitalCity, List.of(cities))`.
- Overrides `cities()` to return a defensive copy.

---

## Code Block 4

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
import java.util.Comparator;
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;

record State(String name) {}
record City(String name, State state) {}

public class StateHistogram {
    public static State stateWithMostCities(List<City> cities) {
        record StateCities(State state, long cityCount) {
            StateCities(Map.Entry<State, Long> entry) {
                this(entry.getKey(), entry.getValue());
            }

            static Comparator<StateCities> comparingByCityCount() {
                return Comparator.comparing(StateCities::cityCount);
            }
        }

        return cities.stream()
                .collect(Collectors.groupingBy(City::state, Collectors.counting()))
                .entrySet().stream()
                .map(StateCities::new)
                .max(StateCities.comparingByCityCount())
                .map(StateCities::state)
                .orElseThrow();
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a Java example that demonstrates a local record declared inside a method to improve the readability of a Stream pipeline. Define simple top-level records `State` and `City`, where each `City` has a `State`. Then create a utility class with a static method that accepts `List<City>` and returns the `State` that has the most cities. Inside that method, declare a local record `StateCities(State state, long cityCount)` with a constructor that converts a `Map.Entry<State, Long>` into the record components and a static comparator factory based on the `cityCount` accessor. Use `Collectors.groupingBy(City::state, Collectors.counting())`, convert the histogram entries to the local record, select the maximum by count, map back to the `State`, and call `orElseThrow()`.

**Suggested Assertions:**
- Declares a local record inside a method, not only top-level records.
- The local record has components `State state` and `long cityCount`.
- Includes a constructor taking `Map.Entry<State, Long>`.
- Uses `Collectors.groupingBy(..., Collectors.counting())`.
- Uses `Comparator.comparing(StateCities::cityCount)` and `max(...)` on the stream.

---
