# Object as a Superclass - Eval Prompts

Source: https://dev.java/learn/inheritance/objects/

---

## Code Block 1

**Score:** 5 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class Book {
    String ISBN;

    public String getISBN() {
        return ISBN;
    }

    public boolean equals(Object obj) {
        return obj instanceof Book book && ISBN.equals(book.getISBN());
    }
}
```

**Prose Rendering (for LLM consumption):**
Define a `Book` class with a field named `ISBN` of type `String` and a getter `getISBN()`. Override `equals(Object obj)` so that it uses Java pattern matching for `instanceof`: test whether `obj instanceof Book book`, and if so compare `this.ISBN` to `book.getISBN()` with `String.equals`. The method should return the boolean result of that combined expression directly. Because the surrounding tutorial explicitly states the `equals`/`hashCode` contract, an equivalent generated solution should also include a compatible `hashCode()` implementation based on the same ISBN field, even though the source snippet only shows `equals()`.

**Suggested Assertions:**
- Declares `boolean equals(Object obj)`.
- Uses `obj instanceof Book book` pattern matching syntax.
- Compares ISBN values with `ISBN.equals(book.getISBN())` or an equivalent field-based comparison.
- Includes a `getISBN()` accessor.
- Also defines `hashCode()` consistent with the ISBN-based equality rule.

---

## Code Block 2

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
// Swing Tutorial, 2nd edition
Book firstBook  = new Book("0201914670");
Book secondBook = new Book("0201914670");
if (firstBook.equals(secondBook)) {
    IO.println("objects are equal");
} else {
    IO.println("objects are not equal");
}
```

**Prose Rendering (for LLM consumption):**
Write a small equality test that creates two distinct `Book` objects with the same ISBN string `0201914670`. Store them in variables `firstBook` and `secondBook`, call `firstBook.equals(secondBook)`, and print `objects are equal` when the comparison succeeds, otherwise print `objects are not equal`. The point of the example is that logical equality should succeed for separate instances when their ISBN data matches.

**Suggested Assertions:**
- Creates two separate `Book` instances with the same ISBN literal.
- Uses `firstBook.equals(secondBook)` rather than `==`.
- Prints both possible messages in `if`/`else` branches.
- The success branch prints `objects are equal`.

---

## Code Block 3

**Score:** 3 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
void printClassName(Object obj) {
    IO.println("The object's" + " class is " +
        obj.getClass().getSimpleName());
}
```

**Prose Rendering (for LLM consumption):**
Define a helper method `printClassName` that accepts a parameter of type `Object`. Inside, call `obj.getClass().getSimpleName()` and print the result prefixed by the text `The object's class is `. The important feature is using `getClass()` from `Object` and then calling `getSimpleName()` on the resulting `Class` object to obtain the runtime type name.

**Suggested Assertions:**
- The parameter type is `Object`.
- Uses `obj.getClass().getSimpleName()`.
- Prints or returns the runtime class name rather than a hard-coded string.

---
