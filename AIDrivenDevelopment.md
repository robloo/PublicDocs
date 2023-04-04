Last Updated 3 April 2023 | License CC BY-SA 4.0

# AI-Driven Development

Test-Driven Development (TDD) is a proven strategy for robust software development. It essentially has the following steps (skipping refactoring and some iterations):

 1. Define the feature and specifications
 2. Write unit tests for the feature (tests fail to start)
 3. Implement the feature following the specifications
 4. Run the unit tests and adjust code until all tests pass

This; however, is very resource intensive and slow. It's common for tests to actually be longer than the feature implementation as well. You need a large team and adequate budgets of time and money to follow this robust process.

Separately, we have a new development with large language model AI such as ChatGPT that can now generate working source code. The question quickly arises: how do you integrate this into a stable production workflow?

AI generated source code, while fast, requires iteration and feedback from developers to get just right. Additionally, while models such as GPT 4 can generate fully functional programs, you don’t really want to blindly put these into production without human oversight and understanding.
Now we are ready to merge these two separate concepts together in what I term “AI-Driven Development”.

Large language models are perfect to accelerate (or automate) each part of the test-driven development steps above. In fact, for each step, the AI language models can take an increasing share of the responsibility away from developers. Let me explain for each:

 1. **Define the feature and specifications** | Carefully Guided
    Developers (or even program managers) can use chat-style language models to quickly take a high-level concept for a feature down into a specific API surface area. Once you have an API and specification design for your feature you are done with this step – and AI is the perfect expert to help in this iterative “discussion”.
 2. **Write unit tests for the feature** | Supervised
    Again, AI language models can take the API defined above and write a good portion of the unit tests. These language models are also perfect for generating randomized testing data. At this point the developer need only supervise the process instead of carefully guiding like in step 1.
 3. **Implement the feature following the specifications** | Automated
    At this step we are prepared to use the full power of AI language model. With clear unit tests proving whether an implementation is correct rather than “looks correct” the AI can be tasked with generating the code for the feature by itself. This is an iterative process though as failures and exceptions from unit tests should be passed back to the AI language model to improve code until all tests pass.
 4. **Run the unit tests and adjust code until all tests pass** | Automated
    This step is run simultaneously along with step 3 above and is entirely automated. There is no need for the developer to participate.
When all tests pass the AI language model has generated verifiably correct code. What took days can now be done much more quickly.

## Where to go from here?

In order to take full advantage of this "AI Driven Development" concept IDEs need to fundamentally change in order to support this workflow.

It is also possible the rate of advancement in AI language-models is so rapid that, given only a high-level concept for a feature, an AI will be able to generate a complete program better than any developer. At this point this workflow is not needed except for the cases where human oversight is always required.

---

This document is licensed CC BY-SA 4.0. For full text see: https://creativecommons.org/licenses/by-sa/4.0/legalcode
