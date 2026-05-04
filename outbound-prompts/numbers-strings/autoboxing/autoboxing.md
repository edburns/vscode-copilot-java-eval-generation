# Autoboxing and Unboxing - Eval Prompts

Source: https://dev.java/learn/numbers-strings/autoboxing/

---

## Code Block 1

**Score:** 5 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
import java.util.ArrayList;
import java.util.List;

public class BoxingDemo {
    public static void main(String[] args) {
        List<Integer> ints = new ArrayList<>();

        for (int i = 0; i < 10; i++) {
            ints.add(i);
        }

        System.out.println(ints);
    }
}
```

**Prose Rendering (for LLM consumption):**
Create a class `BoxingDemo` that demonstrates autoboxing with generics. Import `ArrayList` and `List`, instantiate a `List<Integer>`, loop from `0` through `9` with a primitive `int`, and add each primitive directly to the list without manually calling `Integer.valueOf`. Print the populated list at the end.

**Suggested Assertions:**
- Imports `java.util.List` and `java.util.ArrayList`.
- Declares a `List<Integer>`.
- Uses a primitive `int` loop variable.
- Calls `ints.add(i)` with an `int`, relying on autoboxing.
- Does not manually construct `Integer` objects.

---

## Code Block 2

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
import java.util.List;

public class UnboxingOperatorsDemo {
    public static int sumEven(List<Integer> ints) {
        Integer sum = 0;

        for (Integer i : ints) {
            if (i % 2 == 0) {
                sum += i;
            }
        }

        return sum;
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a class `UnboxingOperatorsDemo` with a static method `sumEven` that accepts `List<Integer>` and returns the sum of the even elements. Initialize the accumulator as `Integer sum = 0`, iterate with an enhanced `for` loop over `Integer` elements, use the remainder operator `%` to test parity, and use `+=` to accumulate the values. The point of the example is that `%` and `+=` force automatic unboxing and boxing around wrapper values.

**Suggested Assertions:**
- Method signature uses `List<Integer>`.
- Declares `Integer sum = 0` instead of primitive `int`.
- Uses `% 2 == 0` on an `Integer`.
- Uses `sum += i` with wrapper types.
- Returns the accumulated total.

---

## Code Block 3

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
import java.util.ArrayList;
import java.util.List;

public class Unboxing {
    public static void main(String[] args) {
        Integer i = -8;

        int absVal = absoluteValue(i);
        System.out.println("absolute value of " + i + " = " + absVal);

        List<Double> ld = new ArrayList<>();
        ld.add(3.1416);

        double pi = ld.get(0);
        System.out.println("pi = " + pi);
    }

    public static int absoluteValue(int i) {
        return (i < 0) ? -i : i;
    }
}
```

**Prose Rendering (for LLM consumption):**
Implement a class named `Unboxing` with a `main` method that demonstrates unboxing through both method invocation and assignment. Start with an `Integer` initialized to `-8`, pass it to a helper method `absoluteValue(int i)` that returns the non-negative value using a ternary operator, and print `absolute value of -8 = 8` style output. Then create a `List<Double>`, add `3.1416` to it, retrieve the first element into a primitive `double` variable named `pi`, and print that value. The key feature is that the wrapper types are converted to primitives automatically.

**Suggested Assertions:**
- Declares `Integer i = -8` and passes it to a method expecting `int`.
- Defines `absoluteValue(int i)` using a ternary operator.
- Creates a `List<Double>` and adds a double literal.
- Assigns `ld.get(0)` directly to a primitive `double` variable.
- Prints both the absolute-value message and the `pi` message.

---
