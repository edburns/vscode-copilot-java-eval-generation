# Eval Prompts Summary Report

> Generated from dev.java/learn content. Use this to prioritize which score-5 blocks to implement first.

## Statistics

| Section | Files | Total Blocks | Score 5 | Score 4 | Score 3 |
|---------|-------|-------------|---------|---------|---------|
| Language Basics | 6 | 16 | 5 | 8 | 3 |
| Classes & Objects | 8 | 18 | 11 | 5 | 2 |
| Records | 1 | 4 | 3 | 1 | 0 |
| Numbers & Strings | 5 | 12 | 1 | 7 | 4 |
| Inheritance | 5 | 14 | 7 | 5 | 2 |
| **TOTAL** | **25** | **64** | **27** | **26** | **11** |

---

## All Score-5 Blocks — Prioritization Guide

Each entry below summarizes what the code block actually tests, its complexity, distinctiveness from other blocks, and suitability for eval conversion.

---

### Language Basics (5 blocks)

| # | File | What It Tests | Lines | Complexity | Distinct From Others? |
|---|------|---------------|-------|------------|----------------------|
| 1 | `using-operators/using-operators.md` Block 1 | **ArithmeticDemo**: all 5 arithmetic operators (`+`,`-`,`*`,`/`,`%`) applied sequentially, printing human-readable equations | ~30 | Low-medium | Yes — only block covering all arithmetic ops in one demo |
| 2 | `controlling-flow/controlling-flow.md` Block 3 | **BreakWithLabelDemo**: labeled `break` exiting nested loops during 2D int array search | ~25 | High | Yes — only labeled-break example, uses 2D arrays |
| 3 | `controlling-flow/controlling-flow.md` Block 4 | **ContinueWithLabelDemo**: labeled `continue` in nested for/while loops searching for substring | ~20 | High | Yes — char-by-char substring search with `continue test;` |
| 4 | `switch-statement/switch-statement.md` Block 3 | **Days-in-month**: multi-case labels + leap-year logic (`%4`,`%100`,`%400`) inside case 2 | ~25 | Medium-high | Yes — combines switch multi-label with nested if/else |
| 5 | `switch-expression/switch-expression.md` Block 1 | **Arrow-style switch expression**: `Day` enum → int, multi-label cases, no default (exhaustive) | ~8 | Medium | Partially overlaps #6 |
| 6 | `switch-expression/switch-expression.md` Block 3 | **yield in block-bodied arm**: method returning switch expression using `yield` in a block case | ~12 | Medium | Yes — only block showing `yield` keyword in switch expr |

#### SME Notes — Language Basics
- **Blocks 2 & 3** (labeled break/continue) are the most distinctive and highest-value for eval because LLMs frequently struggle with labeled control flow.
- **Block 4** (days-in-month with leap year) is a classic "can you combine switch with logic?" test.
- **Blocks 5 & 6** overlap somewhat — if you pick one switch-expression eval, **Block 6 (yield)** is more distinctive since Block 5's arrow syntax is also tested in the enums section.
- **Block 1** (ArithmeticDemo) is foundational but very straightforward — an LLM would rarely fail this.

---

### Classes & Objects (11 blocks)

| # | File | What It Tests | Lines | Complexity | Distinct From Others? |
|---|------|---------------|-------|------------|----------------------|
| 7 | `creating-classes/creating-classes.md` Block 1 | **Bicycle class (public fields)**: 3 fields, constructor, 4 methods including `speed -= decrement` | ~30 | Medium | Overlaps with Block 8 (same class, different access) |
| 8 | `creating-classes/creating-classes.md` Block 3 | **Bicycle (encapsulated)**: private fields + getter/setter pairs | ~35 | Medium | Core encapsulation pattern |
| 9 | `defining-methods/defining-methods.md` Block 2 | **DataArtist overloading**: 4 overloaded `draw()` methods with different param lists | ~12 | Low-medium | Only method-overloading block |
| 10 | `calling-methods-constructors/` Block 1 | **computePayment**: 4-param method using `Math.pow`, staged local variables | ~12 | Medium | Good multi-param + Math.pow example |
| 11 | `calling-methods-constructors/` Block 4 | **moveCircle (pass-by-reference)**: mutates object fields, then reassigns param reference | ~8 | Medium | Only reference-vs-value-semantics block |
| 12 | `creating-objects/creating-objects.md` Block 2 | **Rectangle with 4 constructors**: overloaded constructors using Point, defaults | ~25 | Medium-high | Distinct multi-constructor design |
| 13 | `creating-objects/creating-objects.md` Block 3 | **CreateObjectDemo**: creates objects, accesses fields via dot, calls methods, shared references | ~20 | Medium | Tests object lifecycle usage |
| 14 | `more-on-classes/more-on-classes.md` Block 2 | **Rectangle with `this()` chaining**: no-arg → 2-arg → 4-arg constructor delegation | ~15 | Medium-high | Only constructor-chaining block |
| 15 | `more-on-classes/more-on-classes.md` Block 3 | **Bicycle with static counter**: `private static int numberOfBicycles`, `id = ++numberOfBicycles` | ~35 | Medium-high | Only static-field + instance-ID example |
| 16 | `enums/enums.md` Block 1 | **Enum + exhaustive switch expression**: `DayOfWeek` enum in switch expr, no default | ~10 | Medium | Tests enum + switch-expr integration |
| 17 | `enums/enums.md` Block 2 | **Enum with constructor**: `DayOfWeek("MON"...)`, private final field, getter | ~15 | Medium | Core enum-with-state pattern |
| 18 | `enums/enums.md` Block 3 | **Enum with abstract method**: each constant overrides `doSomething()` | ~12 | Medium-high | Only constant-specific-body example |

#### SME Notes — Classes & Objects
- **Blocks 7 & 8** are variants of the same Bicycle class. Pick **Block 8** (encapsulation) — it's the more important pattern and subsumes Block 7.
- **Block 14** (constructor chaining with `this()`) is highly distinctive — LLMs sometimes produce invalid chains.
- **Block 15** (static counter + instance ID) exercises the static/instance boundary cleanly.
- **Block 18** (enum abstract methods) is unusual and would challenge LLMs that don't know constant-specific class bodies.
- **Block 11** (moveCircle) is a canonical Java interview-style question about reference semantics — very good eval material.
- **Block 9** (method overloading) and **Block 12** (4 constructors) are somewhat mechanical but cover essential Java OOP.

---

### Records (3 blocks)

| # | File | What It Tests | Lines | Complexity | Distinct From Others? |
|---|------|---------------|-------|------------|----------------------|
| 19 | `records/records.md` Block 1 | **Minimal Point record**: `record Point(int x, int y) {}` — the simplest record | ~1 | Trivial | Foundation for #20-21 |
| 20 | `records/records.md` Block 2 | **Range with compact constructor validation**: throws `IllegalArgumentException` | ~6 | Low-medium | Only compact-constructor example |
| 21 | `records/records.md` Block 3 | **State record**: 3 components, defensive copy, multiple constructors, varargs, accessor override | ~20 | High | Most complex record example |

#### SME Notes — Records
- **Block 19** is a one-liner; valuable for "does the LLM know record syntax at all?" but trivial.
- **Block 20** is the sweet spot for compact constructor validation — a very common real-world pattern.
- **Block 21** is the most sophisticated — tests defensive copies, overloaded constructors in records, and accessor overriding. This is the gold standard for record evals.

---

### Numbers & Strings (1 block)

| # | File | What It Tests | Lines | Complexity | Distinct From Others? |
|---|------|---------------|-------|------------|----------------------|
| 22 | `autoboxing/autoboxing.md` Block 1 | **BoxingDemo**: adding primitives to `List<Integer>` in a loop (autoboxing) | ~12 | Low-medium | Only autoboxing-focused block at score 5 |

#### SME Notes — Numbers & Strings
- Only one score-5 block in this entire section. The content is more reference-documentation-style (API methods) than language-feature-focused. The **score-4 blocks** here (palindrome reversal, StringBuilder.reverse(), ValueOfDemo, printf formatting) may be worth reconsidering for inclusion.

---

### Inheritance (7 blocks)

| # | File | What It Tests | Lines | Complexity | Distinct From Others? |
|---|------|---------------|-------|------------|----------------------|
| 23 | `what-is-inheritance/` Block 1 | **Bicycle + MountainBike**: extends, super() call, added field and method | ~50 | Medium | Overlaps with polymorphism blocks |
| 24 | `overriding/overriding.md` Block 1 | **Animal/Cat (hiding vs overriding)**: static method hides, instance method overrides, upcast test | ~20 | Medium-high | Only static-hiding example |
| 25 | `polymorphism/polymorphism.md` Block 1 | **Bicycle/MountainBike/RoadBike hierarchy**: 3-class hierarchy, each overrides `printDescription()`, calls `super.printDescription()` | ~55 | High | Full polymorphism demo |
| 26 | `polymorphism/polymorphism.md` Block 2 | **TestBikes (virtual method invocation)**: declares `Bicycle` vars, assigns subclass instances, calls overridden method | ~12 | Medium | Proves virtual dispatch |
| 27 | `objects/objects.md` Block 1 | **Book equals() with pattern matching**: `obj instanceof Book book` in equals override | ~10 | Medium | Only equals/hashCode override block |
| 28 | `abstract-classes/abstract-classes.md` Block 1 | **GraphicObject abstract class**: mixed concrete + abstract methods | ~8 | Medium | Core abstract-class pattern |

#### SME Notes — Inheritance
- **Blocks 25 & 26** together form the definitive polymorphism eval. Block 25 defines the hierarchy; Block 26 is the test harness proving virtual dispatch. Consider them a pair.
- **Block 24** (Animal/Cat hiding vs overriding) is excellent — it tests a subtle distinction that even experienced developers misunderstand.
- **Block 27** (Book equals with pattern matching instanceof) is modern Java (16+) and very relevant.
- **Block 23** overlaps significantly with Blocks 25/26 and Block 7/8 in the classes section.
- **Block 28** (GraphicObject) is important conceptually but the code is quite schematic (placeholders).

---

## Recommended Top Picks for First Implementation

Based on distinctiveness, LLM challenge level, and coverage breadth:

### Tier 1 — Start Here (highest eval value)

| Priority | Block # | Topic | Why |
|----------|---------|-------|-----|
| **1** | 21 | State record (defensive copy, multi-constructor, varargs) | Most complex single block; tests modern Java 14+ features that LLMs struggle with |
| **2** | 25+26 | Polymorphism hierarchy + TestBikes | The canonical OOP eval; tests extends, super, override, virtual dispatch in one coherent example |
| **3** | 2 | BreakWithLabelDemo (2D array search) | Labeled break is rare in real code; LLMs frequently generate incorrect label placement |
| **4** | 24 | Animal/Cat (static hiding vs instance overriding) | Tests a subtle Java semantic that even humans get wrong |
| **5** | 18 | Enum with abstract methods (constant-specific bodies) | Unusual pattern that LLMs often fail on |

### Tier 2 — High Value

| Priority | Block # | Topic | Why |
|----------|---------|-------|-----|
| 6 | 14 | Rectangle with `this()` constructor chaining | Constructor delegation order is error-prone |
| 7 | 15 | Bicycle with static counter + instance ID | Tests static/instance boundary |
| 8 | 6 | Switch expression with `yield` | Modern Java 14+ exclusive feature |
| 9 | 4 | Days-in-month with leap year | Classic logic-in-switch exercise |
| 10 | 27 | Book equals() with pattern matching instanceof | Modern Java 16+ feature |
| 11 | 11 | moveCircle (reference semantics) | Common misconception about Java pass-by-value |
| 12 | 20 | Range record compact constructor validation | Clean, testable, modern |

### Tier 3 — Solid Coverage

| Priority | Block # | Topic | Why |
|----------|---------|-------|-----|
| 13 | 8 | Encapsulated Bicycle (private + getters) | Fundamental OOP but very mechanical |
| 14 | 17 | Enum with constructor + field | Standard pattern |
| 15 | 3 | ContinueWithLabelDemo | High value but very similar structure to #2 |
| 16 | 12 | Rectangle 4 constructors | Exercises constructor overloading |
| 17 | 22 | BoxingDemo (autoboxing) | Important but simple |

---

## Overlap / Deduplication Notes

Several blocks test overlapping concepts. When pruning, consider:

1. **Bicycle class appears in 4+ files** (creating-classes, more-on-classes, what-is-inheritance, polymorphism). Pick the **most complex version** (Block 15 or 25) rather than the basic version.
2. **Switch expression** appears in both `switch-expression/` and `enums/`. The enum version (Block 16) adds enum exhaustiveness; the standalone version (Block 5) is purer switch-expression syntax.
3. **Records** Blocks 19-21 are progressive. Block 19 is trivially derivable from Block 20 or 21 — only implement Block 21 (or 20+21 as a pair).
4. **Labeled break vs labeled continue** (Blocks 2 & 3) test the same concept family. If you only implement one, pick **Block 2** (labeled break) — it's more commonly needed in practice.

---

## Pipeline Considerations

For your 2-PR-at-a-time agentic pipeline:
- Each eval should be **self-contained** — no dependencies between evals
- Blocks in Tier 1 are all independent of each other
- Typical implementation time per eval: prompt text + 3-6 assertions + any helper scripts
- The State record (Block 21) and Polymorphism pair (Blocks 25+26) are the most complex and may need more assertions
