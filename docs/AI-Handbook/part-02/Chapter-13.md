# Chapter 13 – Why AI Doesn't Know Your Company

In the previous chapter, you completed your first real development workflow with your local AI.

Perhaps you asked it to:

- review a pull request,
- explain an unfamiliar class,
- generate documentation,
- or suggest a refactoring.

The results were probably surprisingly good.

But if you experimented a little longer, you may also have noticed something.

The AI gives excellent **general** advice.

It knows remarkably little about **your** project.

Understanding why is one of the most important concepts in practical AI engineering.

---

# The Problem

Imagine two developers.

The first joins your company on Monday.

The second has worked there for five years.

Both are excellent software engineers.

Which one will produce better code during the first week?

Almost certainly the experienced developer.

Not because they're better programmers.

Because they know things the new developer doesn't.

For example:

- your architecture,
- your coding conventions,
- your naming guidelines,
- your deployment process,
- your business rules,
- your customers,
- your products.

This isn't programming knowledge.

It's **company knowledge**.

---

# Foundation Models Are Surprisingly Similar

A foundation model is in exactly the same position as the new developer.

It already knows:

- C#
- SQL
- REST
- Git
- Docker
- Unit testing
- Design patterns
- Clean Code

But it has never seen:

- your repository,
- your architecture,
- your coding standards,
- your wiki,
- your backlog,
- your product terminology.

In other words...

It already knows **how** to build software.

It doesn't know **how your company builds software.**

---

# General Knowledge vs Domain Knowledge

This distinction is fundamental.

Think of it like this.

## General Knowledge

Knowledge useful in almost every software project.

Examples:

- object-oriented programming,
- dependency injection,
- HTTP,
- asynchronous programming,
- SQL.

Foundation models already know these topics very well.

---

## Domain Knowledge

Knowledge specific to a particular organization or project.

Examples:

- your architecture,
- your naming conventions,
- internal APIs,
- coding guidelines,
- release process,
- business terminology,
- abbreviations,
- project history.

This knowledge exists only inside your organization.

The model cannot guess it.

---

# Software Engineering Analogy

Imagine joining a new company.

On your first day someone asks:

> "Please implement Feature X."

Even if you're an experienced developer, you'll immediately ask questions.

Questions like:

- Where is the architecture documentation?
- Which coding standards do we follow?
- Which framework do we use?
- Is there an existing implementation?
- Which team owns this component?

You aren't lacking programming knowledge.

You're lacking context.

Exactly the same is true for an AI.

---

# Where Does This Knowledge Live?

Think about your own projects.

Where would a new developer learn how your team works?

Probably from documents such as:

- coding guidelines,
- architecture documentation,
- onboarding guides,
- API documentation,
- README files,
- contribution guides,
- design decisions.

Interesting observation:

These are exactly the same documents an AI would benefit from.

---

# The First Temptation

Most beginners solve this problem manually.

Every conversation starts like this:

> Our project uses Clean Architecture.

> We use constructor injection.

> Every public API must be documented.

> We don't use regions.

> Logging must use our internal abstraction.

Then the next day...

They type exactly the same information again.

This works.

But it doesn't scale.

---

# The Better Question

Instead of asking:

> "How do I write a better prompt?"

Ask:

> **"How can I stop repeating the same information?"**

That question marks the transition from using AI to engineering AI.

---

# A Small Thought Experiment

Imagine a new developer joins your team.

Would you answer every question personally for the next five years?

Probably not.

Instead, you'd create reusable resources.

For example:

- an onboarding guide,
- coding standards,
- architecture diagrams,
- development checklists.

Now imagine the new developer could read those resources before asking questions.

They would immediately give much better answers.

The same principle applies to AI.

---

# This Changes How You Think About AI

Many people believe they need a "smarter" model.

Often they don't.

A well-informed 7B model can outperform a poorly informed 70B model for project-specific tasks.

Why?

Because relevance often matters more than raw intelligence.

Giving the model the **right knowledge** is frequently more valuable than giving it **more parameters**.

---

# Common Beginner Mistake

When the AI gives a generic answer, beginners often conclude:

> "The model isn't good enough."

In many cases, that's not the real problem.

The model simply lacks the information that every human colleague on the project already has.

Before replacing the model, ask yourself:

> "Have I given it enough context?"

---

# Engineering Note

As software developers, we naturally separate reusable code from application logic.

We create:

- libraries,
- helper classes,
- shared packages,
- documentation.

The same mindset applies to AI.

Instead of repeatedly writing the same explanations in prompts, we gradually move stable knowledge into reusable resources.

You'll begin building those resources in the next chapter.

---

# Looking Ahead

Now that we've identified the problem, it's time to solve it.

How do you teach your AI about:

- your coding standards,
- your architecture,
- your preferred review style,
- your project structure,
- and your team's way of working?

Fortunately, you don't need to retrain the model.

In the next chapter, we'll start building a small "knowledge layer" around the model using reusable instruction files and project documentation.

You'll discover that the most powerful AI systems are often not the ones with the biggest models—but the ones with the best context.

---

# Search Vocabulary

### Domain Knowledge

**Definition**

Knowledge that is specific to a particular company, project or business domain.

**Compare to**

General programming knowledge that every experienced developer already possesses.

**Example**

Your team's coding guidelines and internal architecture documentation.

---

### Context

**Definition**

The information available to the AI while generating a response.

**Compare to**

Similar to the information available to a developer during a task.

**Example**

Source code, project documentation and your prompt together form the AI's context.

---

### Project Knowledge

**Definition**

A subset of domain knowledge that describes how a particular software project is organized and implemented.

**Example**

Repository structure, architectural decisions and project-specific terminology.

---

# 🎉 Level Up!

You've learned one of the most important principles in practical AI engineering:

A foundation model already knows **software development**.

What it lacks is **your software development**.

Understanding this distinction fundamentally changes how you approach AI.

Instead of immediately looking for a "better" model, you'll first ask:

> **"What information does the model need to do a better job?"**

### Next Level

In the next chapter, you'll begin creating reusable project knowledge.

Rather than repeating coding standards and architectural decisions in every conversation, you'll organize them into resources that can be reused across projects, tools and even different AI models.