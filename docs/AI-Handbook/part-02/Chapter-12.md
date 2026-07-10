# Chapter 12 – Your First Useful AI Workflow

In the previous chapters, you built your own local AI workbench.

You can now:

- run a foundation model locally using Ollama,
- interact with it through Open WebUI,
- and understand how the different components of your AI workbench fit together.

Now comes the interesting part.

Until now, you've mostly been experimenting:

> "Tell me a joke."

> "Explain recursion."

> "Write a SQL query."

Those are useful experiments, but they are not how most software developers use AI every day.

Let's solve a real problem instead.

---

# The Problem

Imagine you're reviewing a pull request from a colleague.

The changes span several files.

The implementation looks reasonable, but you're wondering:

- Did the author forget something?
- Is there duplicated code?
- Does the implementation violate SOLID principles?
- Are there potential bugs?
- Is the naming consistent?
- Could the code be simplified?

Reviewing code takes time.

Wouldn't it be useful to have a second pair of eyes?

This is one of AI's greatest strengths.

Not replacing your judgment.

Supporting it.

---

# A Word About Expectations

Many newcomers expect AI to produce perfect answers.

That's the wrong mindset.

Think of AI as a junior developer.

Sometimes surprisingly brilliant.

Sometimes confidently wrong.

Always requiring human review.

Experienced developers don't ask:

> "Can I trust the AI?"

They ask:

> "How can the AI help me make a better decision?"

That small mindset shift makes AI much more useful.

---

# Example Workflow

Suppose you have the following C# method.

```csharp
public decimal CalculateTotal(Order order)
{
    decimal total = 0;

    foreach(var item in order.Items)
    {
        total += item.Price * item.Quantity;
    }

    return total;
}
```

Open a conversation in Open WebUI.

Paste the code.

Now ask something specific.

For example:

> Review this code as if you were performing a pull request review. Focus on readability, maintainability, possible bugs and opportunities for improvement.

Notice something important.

You didn't ask:

> Is this code good?

Instead, you gave the AI a role and clear review criteria.

That makes a significant difference.

---

# Why This Works

Foundation models have seen enormous amounts of publicly available source code during training.

That means they already know many common software engineering concepts, including:

- clean code
- common design patterns
- unit testing
- REST APIs
- SQL
- Git
- C#
- Java
- Python
- JavaScript

This is why they can often provide surprisingly useful reviews.

However...

---

# ...There Is Something Missing

Suppose your company follows these coding conventions:

- Every public method must be documented.
- Constructor injection is mandatory.
- Exceptions must be logged.
- Nullable reference types are required.
- Every service must use your internal logging abstraction.

Will the AI know those rules?

No.

It has never seen your company.

It has never seen your repository.

It has never read your architecture documentation.

It only knows what you tell it.

This is one of the biggest "AHA!" moments when working with AI.

The model already understands software development.

What it lacks is **your project's domain knowledge**.

We'll solve that in the next chapters.

---

# Improving the Prompt

Suppose the first answer was useful.

Can it become even better?

Certainly.

For example:

> Review this C# code as if you were a senior software engineer. Focus on readability, maintainability, naming, SOLID principles, potential bugs and testability. Explain each recommendation and indicate its priority.

Notice what changed.

You didn't give the AI more code.

You gave it a clearer objective.

Good prompting is usually less about clever wording and more about reducing ambiguity.

---

# Iterate Like a Developer

Rarely is the first response the final one.

Instead, continue the conversation.

For example:

> Explain your second suggestion in more detail.

or

> Can you provide an alternative implementation?

or

> Would you make the same recommendation in a high-performance application?

This should feel familiar.

You're having a technical discussion.

Not executing a command.

---

# Try Other Everyday Tasks

Once you've reviewed your first piece of code, try a few more practical tasks.

For example:

## Explain Existing Code

Paste a method from an unfamiliar project.

Ask:

> Explain this code to a developer who has just joined the team.

---

## Generate Documentation

Paste a public class.

Ask:

> Write XML documentation comments for this class.

---

## Refactor

Ask:

> Suggest improvements without changing the public behaviour.

---

## Write Tests

Ask:

> Generate xUnit tests covering the most important scenarios.

---

## Summarize

Paste a long exception stack trace.

Ask:

> Summarize the likely root cause.

---

Notice a pattern?

The AI isn't replacing you.

It's accelerating work you already know how to do.

---

# Common Beginner Mistake

Many developers ask very broad questions.

For example:

> Improve this code.

The AI now has to guess:

Improve how?

Performance?

Readability?

Security?

Maintainability?

Testing?

Instead, tell the AI what kind of improvement you're looking for.

The more specific the objective, the more useful the answer is likely to be.

---

# Engineering Note

Always review AI-generated code before committing it.

Even when the suggestion looks correct.

AI is an excellent assistant.

It is not a substitute for understanding your own codebase.

Treat generated code the same way you would treat code submitted by a colleague.

Review it.

Test it.

Only then merge it.

---

# Looking Ahead

By now you may have noticed something.

Every conversation starts similarly.

You repeatedly explain:

- your preferred coding style,
- your project's conventions,
- your architectural decisions,
- and the role you want the AI to assume.

Repeating this information quickly becomes tedious.

Fortunately, you don't have to.

In the next chapter, we'll explore why foundation models don't know your company—and how to gradually teach them the context they need to become genuinely useful members of your development workflow.

---

# Search Vocabulary

### Domain Knowledge

**Definition**

Knowledge that is specific to a particular company, project or business domain rather than general programming knowledge.

**Example**

Your team's coding guidelines and architecture decisions are domain knowledge.

---

### Code Review

**Definition**

The process of examining source code to identify defects, improve quality and ensure compliance with team standards.

**Example**

AI can assist with code reviews by highlighting potential issues, but the final decision remains with the developer.

---

### Hallucination

**Definition**

A response in which an AI model presents incorrect or invented information as if it were true.

**Example**

An AI may confidently reference a method or API that does not actually exist.

---

# 🎉 Level Up!

You've completed your first real developer workflow using your local AI assistant.

You can now:

- use AI to review source code,
- generate documentation,
- explain unfamiliar code,
- refactor existing implementations,
- and write more effective prompts by giving the AI a clear role and objective.

More importantly, you've encountered the first real limitation of every foundation model:

It understands **software development** remarkably well.

It does **not** understand **your software development**.

### Next Level

The next chapter explores one of the most important ideas in practical AI engineering:

**How do you teach an AI about your company, your project and your way of working—without repeating yourself in every conversation?**