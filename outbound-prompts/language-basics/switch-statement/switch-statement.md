# Branching with Switch Statements - Eval Prompts

Source: https://dev.java/learn/language-basics/switch-statement/

---

## Code Block 1

**Score:** 4 (canonical traditional `switch` statement with assignment and `break`)

**Original Code:**
```java
int quarter = ...; // any value

String quarterLabel = null;
switch (quarter) {
    case 0: quarterLabel = "Q1 - Winter"; 
            break;
    case 1: quarterLabel = "Q2 - Spring"; 
            break;
    case 2: quarterLabel = "Q3 - Summer"; 
            break;
    case 3: quarterLabel = "Q3 - Summer"; 
            break;
    default: quarterLabel = "Unknown quarter";
};
```

**Prose Rendering (for LLM consumption):**
Write a traditional `switch` statement over an integer variable `quarter`. Before the switch, declare `String quarterLabel = null;`. Inside the switch, use colon-style `case` labels for the values `0`, `1`, `2`, and `3`, assigning season-like quarter labels such as `"Q1 - Winter"` and ending each case with `break;`. Add a `default` branch that assigns `"Unknown quarter"`. The snippet should illustrate the classic pattern of assigning to a variable declared before the switch.

**Suggested Assertions:**
- Declares `String quarterLabel = null` before the switch
- Switches on an integer named `quarter`
- Uses colon-style `case` labels with explicit `break;` statements
- Includes a `default` branch assigning `"Unknown quarter"`

---

## Code Block 2

**Score:** 4 (strong fall-through example that is hard to replace with a simpler construct)

**Original Code:**
```java
int month = 8;
List<String> futureMonths = new ArrayList<>();

switch (month) {
    case 1:  futureMonths.add("January");
    case 2:  futureMonths.add("February");
    case 3:  futureMonths.add("March");
    case 4:  futureMonths.add("April");
    case 5:  futureMonths.add("May");
    case 6:  futureMonths.add("June");
    case 7:  futureMonths.add("July");
    case 8:  futureMonths.add("August");
    case 9:  futureMonths.add("September");
    case 10: futureMonths.add("October");
    case 11: futureMonths.add("November");
    case 12: futureMonths.add("December");
             break;
    default: break;
}
```

**Prose Rendering (for LLM consumption):**
Create a fall-through `switch` example that starts with `int month = 8;` and an empty `List<String> futureMonths = new ArrayList<>();`. Switch on `month`, and for each month number from 1 through 12 add that month's English name to `futureMonths`. Do not put `break` statements between the month cases; allow the code to fall through so that starting at case 8, the list accumulates August through December. Include one `break` after case 12 and a `default` that simply breaks.

**Suggested Assertions:**
- Declares `futureMonths` as `new ArrayList<>()`
- Uses cases `1` through `12` to add month names to the list
- Intentionally omits intermediate `break;` statements to allow fall-through
- Ends with a `break;` after `case 12` and a `default: break;`

---

## Code Block 3

**Score:** 5 (excellent multi-case-label and nested-logic example, including leap-year handling)

**Original Code:**
```java
int month = 2;
int year = 2021;
int numDays = 0;

switch (month) {
    case 1: case 3: case 5:   // January March May
    case 7: case 8: case 10:  // July August October
    case 12:
        numDays = 31;
        break;
    case 4: case 6:   // April June
    case 9: case 11:  // September November
        numDays = 30;
        break;
    case 2: // February
        if (((year % 4 == 0) && 
             !(year % 100 == 0))
             || (year % 400 == 0))
            numDays = 29;
        else
            numDays = 28;
        break;
    default:
        IO.println("Invalid month.");
        break;
}
```

**Prose Rendering (for LLM consumption):**
Write a `switch` statement that computes the number of days in a month. Start with `int month = 2;`, `int year = 2021;`, and `int numDays = 0;`. Group the 31-day months by stacking multiple `case` labels before one assignment to `numDays = 31;`, and group the 30-day months similarly before assigning `30`. For `case 2`, add an `if/else` leap-year check that uses `% 4`, `% 100`, and `% 400` to decide between 29 and 28 days. Add a `default` branch that prints `"Invalid month."`.

**Suggested Assertions:**
- Uses stacked multi-case labels for the 31-day and 30-day month groups
- Handles February separately with leap-year logic
- Checks leap-year rules using `% 4`, `% 100`, and `% 400`
- Assigns `numDays` and uses `break;` in each branch

---

## Code Block 4

**Score:** 4 (important example of `switch` over `String` with normalization)

**Original Code:**
```java
String month = ...; // any month
int monthNumber = -1;

switch (month.toLowerCase()) {
    case "january":
        monthNumber = 1;
        break;
    case "february":
        monthNumber = 2;
        break;
    case "march":
        monthNumber = 3;
        break;
    case "april":
        monthNumber = 4;
        break;
    case "may":
        monthNumber = 5;
        break;
    case "june":
        monthNumber = 6;
        break;
    case "july":
        monthNumber = 7;
        break;
    case "august":
        monthNumber = 8;
        break;
    case "september":
        monthNumber = 9;
        break;
    case "october":
        monthNumber = 10;
        break;
    case "november":
        monthNumber = 11;
        break;
    case "december":
        monthNumber = 12;
        break;
    default: 
        monthNumber = 0;
        break;
}
```

**Prose Rendering (for LLM consumption):**
Create a `switch` statement whose selector is a `String` month name normalized with `month.toLowerCase()`. Initialize `monthNumber` to `-1` before the switch. Add one case for each lowercase month name from `"january"` through `"december"`, assigning the corresponding month number 1 through 12 and breaking after each assignment. Include a `default` branch that sets `monthNumber = 0;`.

**Suggested Assertions:**
- Switches on `month.toLowerCase()` rather than raw `month`
- Includes string case labels for all twelve month names
- Assigns the matching integer month number in each case
- Uses `default` to assign `0`
