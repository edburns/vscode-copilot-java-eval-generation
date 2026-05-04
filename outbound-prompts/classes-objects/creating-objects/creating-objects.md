# Creating and Using Objects - Eval Prompts

Source: https://dev.java/learn/classes-objects/creating-objects/

---

## Code Block 1

**Score:** 3

**Original Code:**
```java
public class Point {
    public int x = 0;
    public int y = 0;
    // a constructor!
    public Point(int a, int b) {
    x = a;
    y = b;
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a public class `Point` with two public integer fields, `x` and `y`, both initialized to `0` at declaration time. Add a two-argument public constructor `Point(int a, int b)` that assigns `x = a` and `y = b`. Keep the class minimal so it serves as a simple reference type used by other object-creation examples.

**Suggested Assertions:**
- Contains a public class named `Point`.
- Declares public `int x = 0` and `int y = 0`.
- Includes a constructor `Point(int a, int b)`.
- Constructor assigns `x = a` and `y = b`.

---

## Code Block 2

**Score:** 5

**Original Code:**
```java
public class Rectangle {
    public int width = 0;
    public int height = 0;
    public Point origin;

    // four constructors
    public Rectangle() {
    origin = new Point(0, 0);
    }
    public Rectangle(Point p) {
    origin = p;
    }
    public Rectangle(int w, int h) {
    origin = new Point(0, 0);
    width = w;
    height = h;
    }
    public Rectangle(Point p, int w, int h) {
    origin = p;
    width = w;
    height = h;
    }

    // a method for moving the rectangle
    public void move(int x, int y) {
    origin.x = x;
    origin.y = y;
    }

    // a method for computing the area of the rectangle
    public int getArea() {
    return width * height;
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a public class `Rectangle` with public integer fields `width` and `height`, both initialized to `0`, plus a public `Point origin` field. Provide four overloaded constructors: a no-argument constructor that creates `origin = new Point(0, 0)`; a one-argument constructor taking `Point p` and assigning `origin = p`; a two-argument constructor taking `int w, int h` that creates a new origin at `(0, 0)` and assigns width and height; and a three-argument constructor taking `Point p, int w, int h` that stores the passed point and dimensions. Also add `move(int x, int y)` that writes to `origin.x` and `origin.y`, and `getArea()` that returns `width * height`.

**Suggested Assertions:**
- Contains a public class named `Rectangle`.
- Declares public fields `width`, `height`, and `origin`.
- Includes four overloaded constructors.
- Uses `new Point(0, 0)` in the no-arg and `(int w, int h)` constructors.
- Includes `move(int x, int y)` and `getArea()`.

---

## Code Block 3

**Score:** 5

**Original Code:**
```java
public class CreateObjectDemo {

    public static void main(String[] args) {

        // Declare and create a point object and two rectangle objects.
        Point originOne = new Point(23, 94);
        Rectangle rectOne = new Rectangle(originOne, 100, 200);
        Rectangle rectTwo = new Rectangle(50, 100);

        // display rectOne's width, height, and area
        IO.println("Width of rectOne: " + rectOne.width);
        IO.println("Height of rectOne: " + rectOne.height);
        IO.println("Area of rectOne: " + rectOne.getArea());

        // set rectTwo's position
        rectTwo.origin = originOne;

        // display rectTwo's position
        IO.println("X Position of rectTwo: " + rectTwo.origin.x);
        IO.println("Y Position of rectTwo: " + rectTwo.origin.y);

        // move rectTwo and display its new position
        rectTwo.move(40, 72);
        IO.println("X Position of rectTwo: " + rectTwo.origin.x);
        IO.println("Y Position of rectTwo: " + rectTwo.origin.y);
    }
}
```

**Prose Rendering (for LLM consumption):**
Write a public demo class `CreateObjectDemo` with a `public static void main(String[] args)` method. In `main`, create one `Point` object named `originOne` with coordinates `(23, 94)`, then create two `Rectangle` objects: `rectOne` from `originOne`, `100`, and `200`, and `rectTwo` from `50` and `100`. Print `rectOne.width`, `rectOne.height`, and `rectOne.getArea()` with labeled `IO.println` statements. Then alias `rectTwo.origin` to `originOne`, print the x and y position through nested field access `rectTwo.origin.x` and `rectTwo.origin.y`, call `rectTwo.move(40, 72)`, and print the updated coordinates again.

**Suggested Assertions:**
- Contains a public class `CreateObjectDemo` with `main`.
- Instantiates `Point` and `Rectangle` objects with `new`.
- Accesses fields through dot notation like `rectOne.width` and `rectTwo.origin.x`.
- Invokes `rectOne.getArea()` and `rectTwo.move(40, 72)`.
- Reassigns `rectTwo.origin = originOne` to demonstrate shared references.

---
