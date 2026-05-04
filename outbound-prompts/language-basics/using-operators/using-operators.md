# Using Operators in Your Programs - Eval Prompts

Source: https://dev.java/learn/language-basics/using-operators/

---

## Code Block 1

**Score:** 5 (core arithmetic-operator coverage that every Java basics eval suite should have)

**Original Code:**
```java
class ArithmeticDemo {

    public static void main (String[] args) {

        int result = 1 + 2;
        // result is now 3
        IO.println("1 + 2 = " + result);
        int original_result = result;

        result = result - 1;
        // result is now 2
        IO.println(original_result + " - 1 = " + result);
        original_result = result;

        result = result * 2;
        // result is now 4
        IO.println(original_result + " * 2 = " + result);
        original_result = result;

        result = result / 2;
        // result is now 2
        IO.println(original_result + " / 2 = " + result);
        original_result = result;

        result = result + 8;
        // result is now 10
        IO.println(original_result + " + 8 = " + result);
        original_result = result;

        result = result % 7;
        // result is now 3
        IO.println(original_result + " % 7 = " + result);
    }
}
```

**Prose Rendering (for LLM consumption):**
Create a class `ArithmeticDemo` with a `main` method. Inside `main`, declare an `int result` initialized to `1 + 2`, print the expression and result, then keep a second variable named `original_result` to remember the value before each subsequent operation. Reassign `result` in sequence using subtraction, multiplication, division, addition, and remainder: `result - 1`, `result * 2`, `result / 2`, `result + 8`, and `result % 7`. After each reassignment, print a string showing the previous value, the operator used, and the new result, and then update `original_result` before the next operator.

**Suggested Assertions:**
- Defines class `ArithmeticDemo` with `main(String[] args)`
- Uses `+`, `-`, `*`, `/`, and `%` on `int` values
- Reuses a `result` variable across multiple assignments
- Prints human-readable equations such as `"1 + 2 = " + result`

---

## Code Block 2

**Score:** 4 (good unary-operator coverage including numeric sign changes and boolean negation)

**Original Code:**
```java
class UnaryDemo {

    public static void main(String[] args) {

        int result = +1;
        // result is now 1
        IO.println(result);

        result--;
        // result is now 0
        IO.println(result);

        result++;
        // result is now 1
        IO.println(result);

        result = -result;
        // result is now -1
        IO.println(result);

        boolean success = false;
        // false
        IO.println(success);
        // true
        IO.println(!success);
    }
}
```

**Prose Rendering (for LLM consumption):**
Create a class `UnaryDemo` with a `main` method that demonstrates several unary operators. Start with `int result = +1;`, print it, then apply postfix decrement and postfix increment on `result`, printing after each change. Next, assign `result = -result;` to demonstrate unary minus and print the negative value. Finally, declare `boolean success = false;`, print the boolean as-is, and then print `!success` to show logical complement.

**Suggested Assertions:**
- Uses unary plus in an initializer: `int result = +1;`
- Applies both `result--` and `result++`
- Uses unary minus in an assignment like `result = -result;`
- Demonstrates boolean negation with `!success`

---

## Code Block 3

**Score:** 4 (important example distinguishing prefix and postfix increment semantics)

**Original Code:**
```java
class PrePostDemo {
    public static void main(String[] args){
        int i = 3;
        i++;
        // prints 4
        IO.println(i);
        ++i;               
        // prints 5
        IO.println(i);
        // prints 6
        IO.println(++i);
        // prints 6
        IO.println(i++);
        // prints 7
        IO.println(i);
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a class `PrePostDemo` with a `main` method that starts with `int i = 3`. Apply a postfix increment `i++;` and print `i`, then apply a prefix increment `++i;` and print again. After that, print the result of `++i` directly inside `IO.println(...)`, then print the result of `i++` directly inside another `IO.println(...)`, and finally print `i` one last time. The purpose is to show that prefix increment evaluates to the incremented value while postfix increment evaluates to the original value.

**Suggested Assertions:**
- Initializes `i` to `3`
- Uses both standalone `i++`/`++i` statements and inline `IO.println(++i)` / `IO.println(i++)`
- Prints after both prefix and postfix forms
- Leaves `i` at `7` by the end of the method

---

## Code Block 4

**Score:** 3 (valuable short-circuit boolean-operator example)

**Original Code:**
```java
class ConditionalDemo1 {

    public static void main(String[] args){
        int value1 = 1;
        int value2 = 2;
        if ((value1 == 1) && (value2 == 2))
            IO.println("value1 is 1 AND value2 is 2");
        if ((value1 == 1) || (value2 == 1))
            IO.println("value1 is 1 OR value2 is 1");
    }
}
```

**Prose Rendering (for LLM consumption):**
Create a class `ConditionalDemo1` with a `main` method that declares `int value1 = 1;` and `int value2 = 2;`. Add one `if` statement using `&&` to check that `value1` equals 1 and `value2` equals 2, printing a message that both conditions are true. Add a second `if` statement using `||` to check whether either `value1` is 1 or `value2` is 1, printing a message that uses `OR` in the text.

**Suggested Assertions:**
- Uses both `&&` and `||`
- Compares `value1` and `value2` with `==`
- Has two separate `if` statements rather than one combined example
- Prints distinct messages for the AND and OR cases

---

## Code Block 5

**Score:** 3 (compact but canonical ternary-operator example)

**Original Code:**
```java
class ConditionalDemo2 {

    public static void main(String[] args){
        int value1 = 1;
        int value2 = 2;
        int result;
        boolean someCondition = true;
        result = someCondition ? value1 : value2;

        IO.println(result);
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a class `ConditionalDemo2` with a `main` method that declares two integer candidates `value1` and `value2`, a separate `int result`, and a boolean named `someCondition` initialized to `true`. Assign `result` using the ternary operator so that it becomes `value1` when `someCondition` is true and `value2` otherwise. Print the resulting integer afterward.

**Suggested Assertions:**
- Declares `boolean someCondition = true`
- Uses the ternary operator `? :` to assign `result`
- Chooses between `value1` and `value2`
- Prints the selected result after the assignment

---

## Code Block 6

**Score:** 4 (strong type-test example spanning class inheritance and interface implementation)

**Original Code:**
```java
class InstanceofDemo {
    public static void main(String[] args) {

        Parent obj1 = new Parent();
        Parent obj2 = new Child();

        IO.println("obj1 instanceof Parent: "
            + (obj1 instanceof Parent));
        IO.println("obj1 instanceof Child: "
            + (obj1 instanceof Child));
        IO.println("obj1 instanceof MyInterface: "
            + (obj1 instanceof MyInterface));
        IO.println("obj2 instanceof Parent: "
            + (obj2 instanceof Parent));
        IO.println("obj2 instanceof Child: "
            + (obj2 instanceof Child));
        IO.println("obj2 instanceof MyInterface: "
            + (obj2 instanceof MyInterface));
    }
}

class Parent {}
class Child extends Parent implements MyInterface {}
interface MyInterface {}
```

**Prose Rendering (for LLM consumption):**
Create a class `InstanceofDemo` with a `main` method plus three top-level types beneath it: an empty `Parent` class, an empty `Child` class that extends `Parent` and implements `MyInterface`, and an empty `MyInterface` interface. In `main`, declare `obj1` as `new Parent()` and `obj2` as `new Child()`, both typed as `Parent`. Print six lines that concatenate descriptive labels with the results of `instanceof` checks testing each object against `Parent`, `Child`, and `MyInterface`.

**Suggested Assertions:**
- Defines `Parent`, `Child extends Parent`, and `interface MyInterface`
- Declares `Parent obj2 = new Child();`
- Uses `instanceof` against both a superclass and an interface
- Prints labeled results for both `obj1` and `obj2`
