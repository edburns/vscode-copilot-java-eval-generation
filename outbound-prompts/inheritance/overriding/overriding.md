# Overriding and Hiding Methods - Eval Prompts

Source: https://dev.java/learn/inheritance/overriding/

---

## Code Block 1

**Score:** 5 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class Animal {
    public static void testClassMethod() {
        IO.println("The static method in Animal");
    }
    public void testInstanceMethod() {
        IO.println("The instance method in Animal");
    }
}

public class Cat extends Animal {
    public static void testClassMethod() {
        IO.println("The static method in Cat");
    }
    public void testInstanceMethod() {
        IO.println("The instance method in Cat");
    }

    public static void main(String[] args) {
        Cat myCat = new Cat();
        Animal myAnimal = myCat;
        Animal.testClassMethod();
        myAnimal.testInstanceMethod();
    }
}
```

**Prose Rendering (for LLM consumption):**
Create a superclass `Animal` with one public static method `testClassMethod()` that prints `The static method in Animal`, and one public instance method `testInstanceMethod()` that prints `The instance method in Animal`. Then create a subclass `Cat extends Animal` that declares another public static method with the same signature printing `The static method in Cat`, and an instance method with the same signature printing `The instance method in Cat`. In `Cat.main`, instantiate `Cat`, upcast it to an `Animal` reference, call `Animal.testClassMethod()` on the class, and call `myAnimal.testInstanceMethod()` on the reference. This example must preserve the contrast between static method hiding and instance method overriding.

**Suggested Assertions:**
- `Cat` extends `Animal`.
- Both classes declare `testClassMethod`, and both methods are `static`.
- Both classes declare `testInstanceMethod`, and the subclass version is an instance method.
- `main` upcasts a `Cat` to an `Animal` reference.
- The code invokes `Animal.testClassMethod()` and `myAnimal.testInstanceMethod()`.

---

## Code Block 2

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public class Horse {
    public String identifyMyself() {
        return "I am a horse.";
    }
}

public interface Flyer {
    default public String identifyMyself() {
        return "I am able to fly.";
    }
}

public interface Mythical {
    default public String identifyMyself() {
        return "I am a mythical creature.";
    }
}

public class Pegasus extends Horse implements Flyer, Mythical {
    public static void main(String... args) {
        Pegasus myApp = new Pegasus();
        IO.println(myApp.identifyMyself());
    }
}
```

**Prose Rendering (for LLM consumption):**
Define a concrete class `Horse` with an instance method `identifyMyself()` returning the string `I am a horse.`. Define two interfaces, `Flyer` and `Mythical`, each with a `default public String identifyMyself()` method returning its own descriptive string. Then define `Pegasus` so that it `extends Horse` and `implements Flyer, Mythical`, but does not override `identifyMyself()`. Its `main` method should create a `Pegasus` instance and print the result of `identifyMyself()`. The example should demonstrate the default-method resolution rule that an inherited class method wins over conflicting interface default methods.

**Suggested Assertions:**
- `Pegasus` is declared as `extends Horse implements Flyer, Mythical`.
- `Flyer` and `Mythical` both contain `default` implementations of `identifyMyself()`.
- `Horse` defines a concrete `identifyMyself()` instance method.
- `Pegasus` does not declare its own `identifyMyself()` override.
- `main` prints `myApp.identifyMyself()`.

---

## Code Block 3

**Score:** 4 (1=minimally acceptable, 5=no Java eval suite would be complete without this)

**Original Code:**
```java
public interface OperateCar {
    // ...
    default public int startEngine(EncryptedKey key) {
        // Implementation
    }
}

public interface FlyCar {
    // ...
    default public int startEngine(EncryptedKey key) {
        // Implementation
    }
}

public class FlyingCar implements OperateCar, FlyCar {
    // ...
    public int startEngine(EncryptedKey key) {
        FlyCar.super.startEngine(key);
        OperateCar.super.startEngine(key);
    }
}
```

**Prose Rendering (for LLM consumption):**
Model a default-method conflict between two interfaces. Define `OperateCar` and `FlyCar`, each with a `default public int startEngine(EncryptedKey key)` method. Then define a class `FlyingCar` that implements both interfaces and therefore must override `startEngine(EncryptedKey key)`. Inside the overriding method, explicitly invoke both inherited default implementations using qualified super calls: `FlyCar.super.startEngine(key);` and `OperateCar.super.startEngine(key);`. The example is schematic, so placeholder comments are acceptable, but the important feature is explicit interface-qualified `super` dispatch to resolve conflicting defaults.

**Suggested Assertions:**
- Both interfaces declare a `default` method named `startEngine` with the same signature.
- `FlyingCar` implements both `OperateCar` and `FlyCar`.
- `FlyingCar` overrides `startEngine(EncryptedKey key)`.
- The method body contains `FlyCar.super.startEngine(key)`.
- The method body contains `OperateCar.super.startEngine(key)`.

---
