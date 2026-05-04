# Calling Methods and Constructors - Eval Prompts

Source: https://dev.java/learn/classes-objects/calling-methods-constructors/

---

## Code Block 1

**Score:** 5

**Original Code:**
```java
public double computePayment(
                  double loanAmt,
                  double rate,
                  double futureValue,
                  int numPeriods) {
    double interest = rate / 100.0;
    double partial1 = Math.pow((1 + interest),
                    - numPeriods);
    double denominator = (1 - partial1) / interest;
    double answer = (-loanAmt / denominator)
                    - ((futureValue * partial1) / denominator);
    return answer;
}
```

**Prose Rendering (for LLM consumption):**
Write a public method `computePayment` that returns `double` and takes four parameters: `double loanAmt`, `double rate`, `double futureValue`, and `int numPeriods`. In the body, compute `interest` as `rate / 100.0`. Then compute `partial1` using `Math.pow((1 + interest), - numPeriods)`. Derive `denominator` as `(1 - partial1) / interest`. Compute `answer` as `(-loanAmt / denominator) - ((futureValue * partial1) / denominator)` and return `answer`. Preserve the use of local `double` variables to stage the calculation.

**Suggested Assertions:**
- Declares `public double computePayment`.
- Uses four parameters with the expected names and types.
- Calls `Math.pow((1 + interest), - numPeriods)`.
- Introduces local variables `interest`, `partial1`, `denominator`, and `answer`.
- Returns `answer`.

---

## Code Block 2

**Score:** 4

**Original Code:**
```java
public Polygon polygonFrom(Point... corners) {
    int numberOfSides = corners.length;
    double squareOfSide1, lengthOfSide1;
    squareOfSide1 = (corners[1].x - corners[0].x)
                     * (corners[1].x - corners[0].x)
                     + (corners[1].y - corners[0].y)
                     * (corners[1].y - corners[0].y);
    lengthOfSide1 = Math.sqrt(squareOfSide1);

    // more method body code follows that creates and returns a
    // polygon connecting the Points
}
```

**Prose Rendering (for LLM consumption):**
Write a method `polygonFrom` that returns `Polygon` and accepts a varargs parameter `Point... corners`. Inside the method, compute `int numberOfSides = corners.length`. Declare two `double` locals named `squareOfSide1` and `lengthOfSide1`. Compute `squareOfSide1` from the first two points using the distance formula expanded into x-difference squared plus y-difference squared, accessing coordinates as `corners[index].x` and `corners[index].y`. Then compute `lengthOfSide1 = Math.sqrt(squareOfSide1)`. Leave the rest of the method as comments indicating that more code creates and returns a polygon.

**Suggested Assertions:**
- Uses varargs syntax `Point... corners`.
- Reads `corners.length` into `numberOfSides`.
- Accesses point coordinates with indexed array-style syntax such as `corners[1].x`.
- Calls `Math.sqrt(squareOfSide1)`.
- Returns `Polygon`.

---

## Code Block 3

**Score:** 4

**Original Code:**
```java
public class PassPrimitiveByValue {

    public static void main(String[] args) {

        int x = 3;

        // invoke passMethod() with
        // x as argument
        passMethod(x);

        // print x to see if its
        // value has changed
        IO.println("After invoking passMethod, x = " + x);

    }

    // change parameter in passMethod()
    public static void passMethod(int p) {
        p = 10;
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a public class `PassPrimitiveByValue` containing a `public static void main(String[] args)` method and a helper `public static void passMethod(int p)`. In `main`, declare `int x = 3`, call `passMethod(x)`, and then print `"After invoking passMethod, x = " + x` using `IO.println`. In `passMethod`, reassign the parameter with `p = 10;` but do not return anything. The example should demonstrate that changing a primitive parameter does not change the caller's local variable.

**Suggested Assertions:**
- Contains a public class named `PassPrimitiveByValue`.
- `main` declares `int x = 3` and calls `passMethod(x)`.
- `passMethod` is `static`, takes an `int`, and assigns `p = 10`.
- The printed message mentions `After invoking passMethod, x = `.
- The code does not return a modified primitive from `passMethod`.

---

## Code Block 4

**Score:** 5

**Original Code:**
```java
public void moveCircle(Circle circle, int deltaX, int deltaY) {
    // code to move origin of circle to x+deltaX, y+deltaY
    circle.setX(circle.getX() + deltaX);
    circle.setY(circle.getY() + deltaY);

    // code to assign a new reference to circle
    circle = new Circle(0, 0);
}
```

**Prose Rendering (for LLM consumption):**
Write an instance method `moveCircle` returning `void` and taking a `Circle circle`, `int deltaX`, and `int deltaY`. First mutate the passed-in object by calling `circle.setX(circle.getX() + deltaX)` and `circle.setY(circle.getY() + deltaY)`. After mutating the original object, reassign the local parameter variable with `circle = new Circle(0, 0);`. The example should preserve the contrast between mutating the referenced object and rebinding the local reference.

**Suggested Assertions:**
- Method signature is `moveCircle(Circle circle, int deltaX, int deltaY)`.
- Uses getter-plus-setter updates on the passed `circle` object.
- Reassigns the parameter variable with `new Circle(0, 0)`.
- Demonstrates both object mutation and local reference reassignment in the same method.

---
