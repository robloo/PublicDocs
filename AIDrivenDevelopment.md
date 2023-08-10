Last Updated 4 April 2023 | License CC BY-SA 4.0

# AI-Driven Development

### Test-Driven Development

Test-Driven Development (TDD) is a proven strategy for software development. It essentially has the following steps:

 1. Define the feature and specifications
 2. Write unit tests for the feature (tests fail to start)
 3. Implement the feature following the specifications
 4. Run the unit tests and adjust code until all tests pass

This; however, is very resource intensive. It's common for tests to require more source code than the feature implementation. You need a large team and adequate budgets of time and money to follow this robust process.

### Large Language Model AI

Separately, we have a new development paradigm using large language model AI that can generate working source code. 

AI generated source code, while quick to generate, requires iteration and feedback from developers to get right (often corrections to match intent). While models such as GPT 4 can generate fully functional programs, you don’t really want to blindly put these into production without human oversight and understanding. Nevertheless, the power and future direction of large language models is already clear. The question arises: how do you integrate AI into a stable production workflow?

Now we are ready to merge these two separate concepts (TDD and AI) together in what I term “AI-Driven Development”.

### AI-Driven Development Workflow

Large language models are perfect to accelerate (or automate) each part of the test-driven development steps above. In fact, for each step, the AI language model can take an increasing share of the responsibility away from developers. Let me explain for each:

 1. **Define the feature and specifications** | Carefully Guided
    
    Developers (or even program managers) can use chat-style language models to quickly take a high-level concept for a feature down into a specific API. Once you have an API and specification design for a feature you are done with this step – and AI is the perfect expert to help in this iterative discussion. This step does require careful guidance of the language model to generate valid specifications.

2. **Write unit tests for the feature** | Supervised
    
    AI language models can take the API defined above and write a good portion of the unit tests. These language models are also perfect for generating randomized, yet logical, testing data. The developer need only supervise this process.

 3. **Implement the feature following the specifications** | Automated
    
    At this step we are prepared to use the full power of AI language models. With clear unit tests proving whether an implementation is correct rather than "looks correct" the AI can be tasked with generating the source code for the feature by itself. This is an iterative process as failures and exceptions from unit tests should be passed back into the AI language model to improve code until all tests pass.

4. **Run the unit tests and adjust code until all tests pass** | Automated
    
    This step is run simultaneously along with step three above and is entirely automated in a closed loop. When all tests pass the AI language model has generated verifiably correct code. The feature is ready for merging into an application.
    
With this process what took days can now be done much more quickly and with a much smaller team.

### The Future

In order to take full advantage of this "AI Driven Development" workflow IDEs need to be adjusted to better support it. This is already coming in the form of plugins such as GitHub Copilot X. However, there is still a lot of opportunitty to streamline these plugins to more explicitly support each of the steps above.

It is also possible the rate of advancement in AI language models is so rapid that, given only a high-level concept for a feature, an AI will be able to generate a complete application or module better than any developer. At this point this workflow is not needed except for cases where human oversight is required for regulatory and/or safety reasons. However, it will remain a great scaffolding to break apart AI code generation ensuring there are always human-comprehensible steps.

---

This document is licensed CC BY-SA 4.0. For full text see: https://creativecommons.org/licenses/by-sa/4.0/legalcode
