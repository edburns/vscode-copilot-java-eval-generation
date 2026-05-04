# String Builders - Eval Prompts

Source: https://dev.java/learn/numbers-strings/string-builders/

---

## Code Block 1

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class StringBuilderDemo {
    public static void main(String[] args) {
        String palindrome = "Dot saw I was Tod";

        StringBuilder sb = new StringBuilder(palindrome);
        sb.reverse();

        System.out.println(sb);
    }
}
```

**Prose Rendering (for LLM consumption):**
Create a class `StringBuilderDemo` that shows how much simpler palindrome reversal becomes with `StringBuilder`. In `main`, store the palindrome text `Dot saw I was Tod` in a `String`, construct a `StringBuilder` from that string, call `reverse()` on the builder, and print the builder directly.

**Suggested Assertions:**
- Constructs `new StringBuilder(palindrome)` from a `String`.
- Calls `reverse()` on the builder.
- Prints the `StringBuilder` instance.
- Uses the same palindrome phrase as the string-based example.

---

## Code Block 2

**Score:** 3 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class StringBuilderOpsDemo {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder(16);
        sb.append("Start");
        sb.append(" middle");
        sb.insert(0, ">> ");
        sb.replace(3, 8, "BEGIN");
        sb.delete(8, 9);
        sb.append(" end");

        System.out.println(sb);
        System.out.println("length=" + sb.length());
        System.out.println("capacity=" + sb.capacity());
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a class `StringBuilderOpsDemo` that demonstrates mutable-string operations beyond `reverse()`. Construct a `StringBuilder` with an explicit initial capacity. Then apply a sequence of mutating operations: append text twice, insert a prefix at the beginning, replace a character range with new text, delete a character range, and append a suffix. Print the final builder contents, then print both its logical length and allocated capacity.

**Suggested Assertions:**
- Uses the `StringBuilder(int)` constructor with an explicit capacity.
- Calls `append`, `insert`, `replace`, and `delete` on the same builder.
- Prints `sb.length()` and `sb.capacity()`.
- Mutates the builder in place rather than creating new `String` objects.

---
