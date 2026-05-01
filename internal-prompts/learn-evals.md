
#### Context

You know that thing "SWEBENCH" https://www.swebench.com/ ?

Well, we have a similar MS internal thing we call "vscbench" It's to evaluate the performance of LLMs within Visual Studio Code at coding tasks. I'm told it's actually used within Anthropic. Anyhow, I am a Java SME and my job is to beef up (from 0) the coverage of the Java developer experience in vscbench. The unit of work in vscbench is an "eval"

Each eval comes in the form of a prompt and a number of assertions to validate that the LLM successfully executed the prompt. Each eval also includes significant boilerplate to configure the execution harness for operation.

Here's an example of a prompt file.

```yaml
# yaml-language-server: $schema=../../../doc/references/TestConfig.schema.json

promptSteps:
  - text: >-
      Fetch the README from
      https://github.com/github/copilot-sdk-java/blob/main/README.md and
      follow the Quick Start instructions to create a Maven project with the
      copilot-sdk-java dependency, write the Quick Start Java code, build it
      with Maven so that it can be run with `java -jar ./target/copilot-sdk-smoketest-1.0-SNAPSHOT.jar`, 
      and run it. When looking at the README, you must only look at the following sections.

      1. **Maven**. This section lists the maven GAV of the `copilot-sdk-java` dependency.
      2. **Quick Start**. This section is the Java code. You must create
         exactly the Java class as written in the **Quick Start** section.

      ❌❌DO NOT LOOK AT ANY OTHER SECTIONS OF THE README.❌❌
    assertions:
      - comment: Verify a pom.xml was created with the copilot-sdk-java dependency
        query: "SELECT COUNT(*) > 0 FROM files WHERE path LIKE '%pom.xml' AND content LIKE '%copilot-sdk-java%'"
      - comment: Verify the Java source file was created with CopilotClient usage
        query: "SELECT COUNT(*) > 0 FROM files WHERE path LIKE '%.java' AND content LIKE '%CopilotClient%'"
      - comment: Verify the agent used the terminal for Maven build or run
        query: SELECT COUNT(*) > 0 FROM toolCalls WHERE tool = 'run_in_terminal' AND
          (args LIKE '%mvn%' OR args LIKE '%mvnw%')
      - comment: Verify the Quick Start program builds and runs with exit code 0
        exec: /eval/run_quickstart.sh
installExtensions: []
vscodeSettings: {}
```

You can see that the prompt file consists of two parts: text and assertions. For discussion let's call these parts "prompt text" and "assertions".

#### My request to you

Now that you know the job to be done, and some low level details on how the evals ultimately must be expressed, let's pop up a level.

This website https://dev.java/learn/ is an authoritative resource on the Java language, from its steward, Oracle.

I want you to scour this authoritative resource and create a set of prompts that will be operated on by other agents, in parallel, and ultimately create evals. 

For each URL:

- For each selected code block, assign a score, from 1 to 5, with 1 being "minimally acceptable value to serve as the basis of an eval" and 5 being "no Java eval suite would be complete without testing for this capability".

- Look for code blocks of sufficient complexity that they can be converted into English prose that can be fed to an LLM such that the LLM would take the prose and create the code. The agent processing the prompts you produce would read the prompts and produce evals: prompt text and assertions.

   Here's an example.
   
   ```java
   var list = List.of("one", "two", "three", "four");
   for (var element: list) {
       IO.println(element);
   }
   ```
   
   As a Java SME, I would cast this into the following prose text:
   
      Use the `var` facility to store the return from the `List.of` facility for the values "one" through "four". 

      Use the enhanced for loop to iterate over the elements of the list.

      Print each element with the `IO.println` facility.
      
- Include both the code block and the prose rendering.

- Include a section of suggested assertions for that code block. For the previous example assertions could be

   - Contains the string `var`.
   
   - Uses the enhanced for loop.
   
   - Uses `List.of`.
   
- Only include codeblocks that demonstrate some language feature in a non-trivial way.

#### Mechanics

Store your output as markdown files in dynamically created subdirectories of the `outbound-prompts` directory, with a subdirectory for each path segment of the URL **after** https://dev.java/learn . For example, when you are processing https://dev.java/learn/classes-objects/calling-methods-constructors/ , you would create the directory `outbound-prompts/classes-objects/calling-methods-constructors` and in that directory you would create a markdown file `calling-methods-constructors.md`

In each such file you would have sections for each selected code block, and you would include the score for each code block.

#### The URLs

Use some kind of "fetch" tool to fetch each of these. Use some kind of "file read" tool to read and understand the content.

https://dev.java/learn/language-basics/using-var/

https://dev.java/learn/language-basics/using-operators/

https://dev.java/learn/language-basics/expressions-statements-blocks/

https://dev.java/learn/language-basics/controlling-flow/

https://dev.java/learn/language-basics/switch-statement/

https://dev.java/learn/language-basics/switch-expression/

https://dev.java/learn/classes-objects/creating-classes/

https://dev.java/learn/classes-objects/defining-methods/

https://dev.java/learn/classes-objects/defining-constructors/

https://dev.java/learn/classes-objects/calling-methods-constructors/

https://dev.java/learn/classes-objects/creating-objects/

https://dev.java/learn/classes-objects/more-on-classes/

https://dev.java/learn/classes-objects/enums/

https://dev.java/learn/classes-objects/design-best-practices/

https://dev.java/learn/records/

https://dev.java/learn/numbers-strings/numbers/

https://dev.java/learn/numbers-strings/characters/

https://dev.java/learn/numbers-strings/strings/

https://dev.java/learn/numbers-strings/string-builders/

https://dev.java/learn/numbers-strings/autoboxing/

https://dev.java/learn/inheritance/what-is-inheritance/

https://dev.java/learn/inheritance/overriding/

https://dev.java/learn/inheritance/polymorphism/

https://dev.java/learn/inheritance/objects/

https://dev.java/learn/inheritance/abstract-classes/

Up to and including **Inheritance** in **Getting to Know the Language** in https://dev.java/learn/ .

#### Final advice

Remember that the prompts you are creating will be operated on by LLM agentic coding agents. Be sufficiently clear to maximize understanding.
