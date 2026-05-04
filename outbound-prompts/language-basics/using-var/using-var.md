# Using the Var Type Identifier - Eval Prompts

Source: https://dev.java/learn/language-basics/using-var/

---

## Code Block 1

**Score:** 4 (clear coverage of local variable type inference in ordinary code and enhanced for loops)

**Original Code:**
```java
var list = List.of("one", "two", "three", "four");
for (var element: list) {
    IO.println(element);
}
```

**Prose Rendering (for LLM consumption):**
Declare a local variable named `list` using the `var` type identifier and initialize it with `List.of(...)` containing the four string literals `"one"`, `"two"`, `"three"`, and `"four"`. Then iterate over that list with an enhanced `for` loop whose loop variable is also declared with `var` and named `element`. Inside the loop body, print each inferred `String` element with `IO.println(element);`.

**Suggested Assertions:**
- Contains a local declaration using `var` with `List.of("one", "two", "three", "four")`
- Uses an enhanced `for` loop with `var` for the loop variable
- Iterates over the previously declared list variable
- Prints each element inside the loop body

---

## Code Block 2

**Score:** 4 (important example of `var` in try-with-resources with inferred resource types)

**Original Code:**
```java
var path = Path.of("debug.log");
try (var stream = Files.newInputStream(path)) {
    // process the file
}
```

**Prose Rendering (for LLM consumption):**
Create a local variable named `path` with `var`, initialized from `Path.of("debug.log")`, so the compiler infers `Path`. Immediately follow that with a `try`-with-resources statement whose resource variable is also declared with `var` and named `stream`, initialized by calling `Files.newInputStream(path)`, which infers `InputStream`. The body of the `try` block is intentionally minimal and just represents processing the file.

**Suggested Assertions:**
- Declares `path` with `var` and initializes it via `Path.of("debug.log")`
- Uses `try (`...`)` with a resource declared as `var stream = Files.newInputStream(path)`
- Reuses the `path` variable when opening the stream
- Demonstrates `var` in a try-with-resources context, not just a normal local variable

---

## Code Block 3

**Score:** 3 (useful negative example capturing `var` restrictions on fields and parameters)

**Original Code:**
```java
public class User  {
    private var name = "Sue"; // COMPILER ERROR

    public void setName(var name) {
        this.name = name;
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a small class named `User` that intentionally does not compile because it misuses `var`. Inside the class, declare a field `name` as `private var name = "Sue";` and annotate it with a compiler-error comment. Also add a setter method `setName` whose parameter is incorrectly declared as `var name`. Inside the method body, assign the parameter to the field with `this.name = name;`. The point of the example is to show that `var` is not legal for fields or method parameters.

**Suggested Assertions:**
- Defines a `User` class
- Includes a field declared with `private var name = "Sue";`
- Includes a method parameter declared with `var name`
- Clearly presents the snippet as a compiler-error example about illegal `var` locations

---

## Code Block 4

**Score:** 3 (useful negative example showing that `var` requires an initializer)

**Original Code:**
```java
public String greetings(int message) {
    var greetings; // COMPILER ERROR
    if (message == 0) {
        greetings = "morning";
    } else {
        greetings = "afternoon";
    }
    return "Good " + greetings;
}
```

**Prose Rendering (for LLM consumption):**
Create a method `greetings` that takes an `int` parameter named `message` and returns `String`. Inside the method, intentionally declare a local variable as `var greetings;` with a compiler-error comment and no initializer. Then use an `if/else` statement: if `message == 0`, assign `"morning"` to `greetings`; otherwise assign `"afternoon"`. Finish by returning the concatenated string `"Good " + greetings`. The example is specifically meant to demonstrate that `var` cannot be used without an initializer, even if all later assignments are obvious to a reader.

**Suggested Assertions:**
- Contains a method returning `String` and accepting `int message`
- Declares `var greetings;` without an initializer
- Uses an `if/else` to assign either `"morning"` or `"afternoon"`
- Returns a concatenated greeting based on the variable assigned later
