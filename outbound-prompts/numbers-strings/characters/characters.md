# Characters - Eval Prompts

Source: https://dev.java/learn/numbers-strings/characters/

---

## Code Block 1

**Score:** 3 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class CharacterDemo {
    public static void main(String[] args) {
        char ch = 'a';

        System.out.println(Character.isLetter(ch));
        System.out.println(Character.isDigit(ch));
        System.out.println(Character.isWhitespace(ch));
        System.out.println(Character.isUpperCase(ch));
        System.out.println(Character.toUpperCase(ch));
        System.out.println(Character.toLowerCase('A'));
        System.out.println(Character.toString(ch));
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a small Java class named `CharacterDemo` with a `main` method that demonstrates static utility methods on `java.lang.Character`. Declare a primitive `char` variable initialized to a lowercase letter and print the results of checking whether it is a letter, digit, whitespace, and uppercase. Then print the uppercase version of that character, the lowercase version of an uppercase literal, and a one-character `String` created with `Character.toString`.

**Suggested Assertions:**
- Declares a primitive `char` variable.
- Calls `Character.isLetter`, `Character.isDigit`, `Character.isWhitespace`, and `Character.isUpperCase`.
- Uses both `Character.toUpperCase` and `Character.toLowerCase`.
- Calls `Character.toString` on a `char`.
- Uses static `Character` methods rather than instance methods.

---

## Code Block 2

**Score:** 2 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class EscapeSequenceDemo {
    public static void main(String[] args) {
        System.out.println("First line\nSecond line");
        System.out.println("Column1\tColumn2");
        System.out.println("She said \"Hello!\" to me.");
        System.out.println("A backslash looks like this: \\");
    }
}
```

**Prose Rendering (for LLM consumption):**
Create a class `EscapeSequenceDemo` whose `main` method prints several string literals containing Java escape sequences. Include one line that embeds a newline escape, one that embeds a tab escape, one that prints double quotes inside the string using escaped quotes, and one that prints a literal backslash using `\\` inside the source.

**Suggested Assertions:**
- Contains string literals with `\n`, `\t`, `\"`, and `\\` escape sequences.
- Uses `System.out.println` calls to demonstrate the escapes.
- Includes a string that prints quoted text such as `"Hello!"`.
- Includes a string that prints a literal backslash.

---
