# When to Use Nested Classes, Local Classes, Anonymous Classes, and Lambda Expressions - Eval Prompts

Source: https://dev.java/learn/classes-objects/design-best-practices/

---

This source page is design guidance only. It does not contain non-trivial Java code blocks suitable for reconstruction-style eval prompts.

Key guidance covered by the page:
- Prefer a local class when you need multiple instances, constructor access, or a named type.
- Prefer an anonymous class when you need extra fields or methods.
- Prefer a lambda expression for a single unit of behavior or a simple functional-interface instance.
- Prefer a nested class when the type should be more widely available.
- Choose a non-static nested class when access to an enclosing instance is required; otherwise prefer a static nested class.
