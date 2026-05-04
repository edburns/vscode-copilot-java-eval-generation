# Numbers - Eval Prompts

Source: https://dev.java/learn/numbers-strings/numbers/

---

## Code Block 1

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
import java.util.Calendar;
import java.util.Locale;

public class TestFormat {
    public static void main(String[] args) {
        long n = 461012;
        System.out.format("%d%n", n);
        System.out.format("%08d%n", n);
        System.out.format("%+8d%n", n);
        System.out.format("%,8d%n", n);
        System.out.format("%+,8d%n%n", n);

        double pi = Math.PI;
        System.out.format("%f%n", pi);
        System.out.format("%.3f%n", pi);
        System.out.format("%10.3f%n", pi);
        System.out.format("%-10.3f%n", pi);
        System.out.format(Locale.FRANCE, "%-10.4f%n%n", pi);

        Calendar c = Calendar.getInstance();
        System.out.format("%tB %te, %tY%n", c, c, c);
        System.out.format("%tl:%tM %tp%n", c, c, c);
        System.out.format("%tD%n", c);
    }
}
```

**Prose Rendering (for LLM consumption):**
Create a class named `TestFormat` with a `main` method that demonstrates numeric and date/time formatting using `System.out.format`. Import `java.util.Calendar` and `java.util.Locale`. Format a `long` value with plain decimal, zero padding, explicit sign, grouping separators, and a combined sign-plus-grouping format. Then format `Math.PI` as a floating-point number using default precision, three decimal places, right-justified width, left-justified width, and a locale-aware call using `Locale.FRANCE`. Finally, obtain the current time from `Calendar.getInstance()` and print the month name, day, year, time, and short date using `%t` conversions.

**Suggested Assertions:**
- Imports `Calendar` and `Locale`.
- Uses `System.out.format` or `printf` with `%d`, `%08d`, `%+8d`, and `%,8d`.
- Formats `Math.PI` with precision specifiers such as `%.3f` and width specifiers such as `%10.3f`.
- Includes a locale-specific formatting call using `Locale.FRANCE`.
- Uses `%t` date/time format specifiers with a `Calendar` instance.

---

## Code Block 2

**Score:** 3 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
import java.text.DecimalFormat;

public class DecimalFormatDemo {
    static void customFormat(String pattern, double value) {
        DecimalFormat myFormatter = new DecimalFormat(pattern);
        String output = myFormatter.format(value);
        System.out.println(value + "  " + pattern + "  " + output);
    }

    public static void main(String[] args) {
        customFormat("###,###.###", 123456.789);
        customFormat("###.##", 123456.789);
        customFormat("000000.000", 123.78);
        customFormat("$###,###.###", 12345.67);
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a class named `DecimalFormatDemo` that imports `java.text.DecimalFormat` and demonstrates custom number-format patterns. Add a helper method `customFormat(String pattern, double value)` that constructs a `DecimalFormat`, formats the numeric value, and prints the original number, the pattern, and the formatted result. In `main`, invoke that helper with patterns that show grouping separators, rounding, zero padding, and a literal dollar-sign prefix.

**Suggested Assertions:**
- Imports `java.text.DecimalFormat`.
- Declares a helper method taking `String pattern` and `double value`.
- Constructs `new DecimalFormat(pattern)`.
- Calls `format(value)` on the formatter.
- Demonstrates patterns `###,###.###`, `###.##`, `000000.000`, and `$###,###.###`.

---

## Code Block 3

**Score:** 3 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class BasicMathDemo {
    public static void main(String[] args) {
        double a = -191.635;
        double b = 43.74;
        int c = 16, d = 45;

        System.out.printf("The absolute value of %.3f is %.3f%n", a, Math.abs(a));
        System.out.printf("The ceiling of %.2f is %.0f%n", b, Math.ceil(b));
        System.out.printf("The floor of %.2f is %.0f%n", b, Math.floor(b));
        System.out.printf("The rint of %.2f is %.0f%n", b, Math.rint(b));
        System.out.printf("The max of %d and %d is %d%n", c, d, Math.max(c, d));
        System.out.printf("The min of %d and %d is %d%n", c, d, Math.min(c, d));
    }
}
```

**Prose Rendering (for LLM consumption):**
Implement a class `BasicMathDemo` with a `main` method that demonstrates several static methods from `java.lang.Math`. Use two `double` variables and two `int` variables. Print formatted sentences showing the results of `Math.abs`, `Math.ceil`, `Math.floor`, `Math.rint`, `Math.max`, and `Math.min`. Use `System.out.printf` with precision specifiers so the numeric output is rounded consistently.

**Suggested Assertions:**
- Uses `Math.abs`, `Math.ceil`, `Math.floor`, `Math.rint`, `Math.max`, and `Math.min`.
- Calls the methods statically through `Math`.
- Uses `System.out.printf` with `%n` line separators.
- Includes both floating-point and integer examples.
- Stores sample values in local variables before printing.

---
