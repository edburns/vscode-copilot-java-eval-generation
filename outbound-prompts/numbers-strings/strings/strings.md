# Strings - Eval Prompts

Source: https://dev.java/learn/numbers-strings/strings/

---

## Code Block 1

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class StringDemo {
    public static void main(String[] args) {
        String palindrome = "Dot saw I was Tod";
        int len = palindrome.length();
        char[] tempCharArray = new char[len];
        char[] charArray = new char[len];

        for (int i = 0; i < len; i++) {
            tempCharArray[i] = palindrome.charAt(i);
        }

        for (int j = 0; j < len; j++) {
            charArray[j] = tempCharArray[len - 1 - j];
        }

        String reversePalindrome = new String(charArray);
        System.out.println(reversePalindrome);
    }
}
```

**Prose Rendering (for LLM consumption):**
Implement a class called `StringDemo` that reverses a palindrome using only `String`, `charAt`, arrays, and loops. In `main`, store the sentence `Dot saw I was Tod` in a `String`, compute its length, allocate two `char[]` arrays of that length, copy characters from the string into the first array with a forward loop, populate the second array in reverse order with a second loop, build a new `String` from the reversed array, and print it.

**Suggested Assertions:**
- Declares a `String` variable initialized to `Dot saw I was Tod`.
- Uses `length()` and `charAt(...)` on the string.
- Allocates two `char[]` arrays.
- Uses two indexed `for` loops, one for copying and one for reversing.
- Constructs the reversed value with `new String(charArray)`.

---

## Code Block 2

**Score:** 3 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class FormatDemo {
    public static void main(String[] args) {
        String fs = String.format(
                "The value of the float variable is %f, while the value of the integer variable is %d, and the string is %s",
                1.0f, 1, "string");
        System.out.println(fs);
    }
}
```

**Prose Rendering (for LLM consumption):**
Create a class `FormatDemo` with a `main` method that demonstrates `String.format`. Build a formatted string using one `%f` placeholder for a floating-point value, one `%d` placeholder for an integer, and one `%s` placeholder for a string literal. Assign the formatted result to a local variable and print it afterward, rather than formatting directly in the print call.

**Suggested Assertions:**
- Calls `String.format(...)`.
- Uses `%f`, `%d`, and `%s` in the format string.
- Stores the formatted result in a `String` local variable.
- Prints the formatted string in a separate statement.

---

## Code Block 3

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class ValueOfDemo {
    public static void main(String[] args) {
        if (args.length == 2) {
            float a = (Float.valueOf(args[0])).floatValue();
            float b = (Float.valueOf(args[1])).floatValue();

            System.out.println("a + b = " + (a + b));
            System.out.println("a - b = " + (a - b));
            System.out.println("a * b = " + (a * b));
            System.out.println("a / b = " + (a / b));
            System.out.println("a % b = " + (a % b));
        } else {
            System.out.println("This program requires two command-line arguments.");
        }
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a command-line program `ValueOfDemo` that expects exactly two arguments. When two arguments are present, convert each string argument to a `Float` using `Float.valueOf`, immediately unbox each wrapper with `.floatValue()`, store the primitive results in `float` locals `a` and `b`, and print the results of addition, subtraction, multiplication, division, and remainder. If the wrong number of arguments is supplied, print a fallback message saying the program requires two command-line arguments.

**Suggested Assertions:**
- Checks `args.length == 2` before doing arithmetic.
- Uses `Float.valueOf(args[index])` and `.floatValue()`.
- Stores values in `float a` and `float b`.
- Prints results for `+`, `-`, `*`, `/`, and `%`.
- Has an `else` branch with an error/help message.

---

## Code Block 4

**Score:** 3 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class ToStringDemo {
    public static void main(String[] args) {
        double d = 858.48;
        String s = Double.toString(d);

        int dot = s.indexOf('.');

        System.out.println(dot + " digits before decimal point.");
        System.out.println((s.length() - dot - 1) + " digits after decimal point.");
    }
}
```

**Prose Rendering (for LLM consumption):**
Create a class `ToStringDemo` that converts a `double` to its string representation and then analyzes that string. Store a sample `double`, call `Double.toString(d)` to obtain a `String`, find the decimal-point index with `indexOf('.')`, and print how many digits appear before and after the decimal point using string length arithmetic.

**Suggested Assertions:**
- Uses `Double.toString(...)`.
- Calls `indexOf('.')` on the resulting string.
- Computes digits before the decimal using the dot index.
- Computes digits after the decimal using `s.length() - dot - 1`.
- Prints both counts.

---

## Code Block 5

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class Filename {
    private final String fullPath;
    private final char pathSeparator;
    private final char extensionSeparator;

    public Filename(String fullPath, char pathSeparator, char extensionSeparator) {
        this.fullPath = fullPath;
        this.pathSeparator = pathSeparator;
        this.extensionSeparator = extensionSeparator;
    }

    public String extension() {
        int dot = fullPath.lastIndexOf(extensionSeparator);
        return fullPath.substring(dot + 1);
    }

    public String filename() {
        int dot = fullPath.lastIndexOf(extensionSeparator);
        int sep = fullPath.lastIndexOf(pathSeparator);
        return fullPath.substring(sep + 1, dot);
    }

    public String path() {
        int sep = fullPath.lastIndexOf(pathSeparator);
        return fullPath.substring(0, sep);
    }
}
```

**Prose Rendering (for LLM consumption):**
Implement a small utility class named `Filename` that stores a full path string plus configurable path and extension separator characters. Make the fields `final`. Provide a constructor that initializes all three fields. Add an `extension()` method that uses `lastIndexOf` and `substring` to return the file extension without the dot, a `filename()` method that returns the base filename between the last path separator and the last extension separator, and a `path()` method that returns the directory portion before the final path separator.

**Suggested Assertions:**
- Declares fields for the full path and two separator characters.
- Uses `lastIndexOf(...)` in each accessor method.
- Uses `substring(...)` to slice the extension, filename, and path.
- `filename()` computes both the separator index and the dot index.
- The fields are immutable after construction.

---

## Code Block 6

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class TextBlockDemo {
    public static void main(String[] args) {
        String query = """
                SELECT "EMP_ID", "LAST_NAME"
                FROM "EMPLOYEE_TB"
                WHERE "CITY" = 'INDIANAPOLIS'
                ORDER BY "EMP_ID", "LAST_NAME";
                """;

        System.out.println(query);
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a Java SE 15+ example named `TextBlockDemo` that demonstrates a text block. Inside `main`, declare a `String` variable assigned from a triple-quoted text block containing a multi-line SQL query. Preserve embedded double quotes around identifiers and a single-quoted city literal. After the text block, print the resulting string.

**Suggested Assertions:**
- Uses Java text block syntax with triple double quotes.
- Stores the text block in a `String` variable.
- Contains multiple lines of SQL-like text.
- Preserves embedded double quotes inside the text block without escaping them.
- Prints the resulting string.

---
