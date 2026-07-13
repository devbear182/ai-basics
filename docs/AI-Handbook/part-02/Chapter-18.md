# Chapter 18 – Agents: Letting AI Coordinate Work

In the previous chapter, you learned how to package recurring tasks into reusable Skills.

That alone is already a significant productivity boost.

Instead of repeatedly describing *how* a task should be performed, you simply execute the appropriate Skill.

Soon, however, you'll notice another pattern.

Many real-world tasks consist of **multiple** Skills.

You no longer want the AI to perform just one step.

You want it to complete an entire workflow.

This is where Agents enter the picture.

---

# The Problem

Imagine you're asked to investigate a production bug.

You don't immediately start writing code.

Instead, you naturally follow a process.

Perhaps something like this:

```
Read bug report

↓

Locate relevant code

↓

Understand implementation

↓

Identify possible cause

↓

Suggest solution

↓

Generate unit tests

↓

Document findings
```

Notice something important.

Every individual step could already be handled by a Skill.

The challenge isn't performing the steps.

The challenge is coordinating them.

---

# What Is an Agent?

An **Agent** is an AI system that can plan and coordinate multiple actions in order to achieve a larger objective.

Unlike a Skill, which performs a single well-defined task, an Agent decides:

- what to do first,
- what information it needs,
- which Skill to use,
- which tools to call,
- whether additional work is required,
- and when the task is complete.

Think of a Skill as an individual tool.

Think of an Agent as the person deciding which tools to use.

---

# A Software Engineering Analogy

Imagine building a web application.

You probably have many reusable components:

- repositories,
- services,
- validators,
- loggers,
- HTTP clients.

None of these components decides when it should execute.

Something coordinates them.

Usually that's your application logic.

The relationship is remarkably similar.

```
Agent

├── Skill A
├── Skill B
├── Skill C
├── Tool A
├── Tool B
└── Memory
```

The Agent is the orchestrator.

The Skills are the reusable building blocks.

---

# A Practical Example

Suppose you ask:

> Investigate why users sometimes receive duplicate invoices.

A simple chat model might answer:

> Please provide the relevant code.

An Agent can approach the problem differently.

For example:

```
Locate invoice generation

↓

Inspect recent changes

↓

Read logging configuration

↓

Find duplicate execution paths

↓

Summarise findings

↓

Suggest possible fixes

↓

Generate regression tests
```

Notice how the Agent continuously decides what to do next.

You provided the objective.

The Agent planned the process.

---

# Agents Don't Replace Skills

This is a common misunderstanding.

Some beginners believe Agents are simply "better Skills."

They aren't.

They solve a different problem.

```
Prompt

↓

One request

↓

One response
```

```
Skill

↓

One reusable workflow

↓

Consistent execution
```

```
Agent

↓

One objective

↓

Many coordinated actions
```

As your AI system grows, you usually need all three.

---

# What Gives an Agent Its Power?

An Agent becomes useful because it combines several capabilities.

Typically, an Agent has access to:

- instructions,
- Skills,
- tools,
- project knowledge,
- conversation context,
- and sometimes memory.

It can choose which of these resources to use while working toward its goal.

The Agent itself is often surprisingly small.

Its effectiveness comes from coordinating everything around it.

---

# Planning Before Acting

One of the most valuable characteristics of a good Agent is that it plans before taking action.

Imagine a senior developer receiving a large feature request.

They don't immediately start typing code.

Instead, they first think:

- Which parts of the system are affected?
- Which documentation should I read?
- What are the risks?
- Do I need clarification?
- Which tests already exist?

An Agent should behave similarly.

Planning generally leads to better results than immediately acting on incomplete information.

---

# Human in the Loop

Although Agents can automate many workflows, they should not automatically make important decisions.

Especially when an Agent can:

- modify source code,
- execute commands,
- delete files,
- create commits,
- deploy software,

human review remains essential.

Think of an Agent as a highly capable junior developer.

It can perform substantial work.

But significant decisions should still be reviewed by an experienced engineer.

---

# Levels of Autonomy

Not all Agents are equally autonomous.

A useful way to think about them is as different autonomy levels.

```
Level 0

Answer questions.
```

```
Level 1

Execute one Skill.
```

```
Level 2

Coordinate several Skills.
```

```
Level 3

Plan workflows independently.
```

```
Level 4

Modify files with approval.
```

```
Level 5

Perform large workflows with minimal supervision.
```

Notice that each level builds upon the previous one.

There is no need to jump directly to Level 5.

Most developers gain tremendous value already at Levels 2 and 3.

---

# The "YOLO" Temptation

Many modern AI tools offer settings that allow the Agent to perform actions without confirmation.

Examples include:

- automatically editing files,
- executing shell commands,
- creating commits,
- deleting generated files.

These modes are often marketed as making the Agent "fully autonomous."

While they can be useful in controlled environments, they should be approached carefully.

An incorrect command can modify hundreds of files in seconds.

The speed of automation also increases the speed at which mistakes can spread.

---

# Guard Rails

As software engineers, we rarely deploy code without safeguards.

The same principle applies to Agents.

Useful guard rails include:

- read-only repositories for exploration,
- confirmation before modifying files,
- restricted terminal commands,
- sandbox environments,
- version control,
- automatic backups,
- human approval before commits.

The goal is not to limit the Agent unnecessarily.

The goal is to ensure that mistakes remain inexpensive to recover from.

---

# Engineering Note

When developers first discover Agents, they often ask:

> "How autonomous can I make it?"

A better question is:

> "How autonomous should it be?"

The answer depends on the task.

Explaining documentation requires very little risk.

Deploying production software requires considerably more.

Design your Agent's permissions according to the consequences of failure.

---

# Behind the Scenes

Although Agents often appear highly autonomous, they usually operate in a simple loop:

```
Plan

↓

Select Tool

↓

Execute

↓

Observe Result

↓

Update Plan

↓

Repeat
```

Many agent frameworks differ mainly in how they implement this loop—not in the underlying language model itself.

---

# Looking Ahead

Your Agent can now coordinate work across multiple Skills and tools.

But another challenge soon appears.

Some information disappears as soon as the conversation ends.

The next day, the Agent no longer remembers:

- previous investigations,
- project decisions,
- your personal preferences,
- recurring problems.

How can an AI build experience over time?

The answer is **Memory**.

---

# Search Vocabulary

### Agent

**Definition**

An AI component that plans and coordinates multiple actions, Skills and tools to achieve a larger objective.

**Compare to**

Similar to an application service that orchestrates several reusable components to complete a business process.

**Example**

An Agent investigating a production bug may search the repository, inspect relevant files, generate a summary and propose fixes without the developer specifying each individual step.

---

### Orchestration

**Definition**

The coordination of multiple components so they work together toward a common objective.

**Compare to**

Similar to an application service coordinating repositories, domain services and external APIs.

**Example**

An Agent deciding which Skill to execute first based on the current task.

---

### Autonomy

**Definition**

The degree to which an AI system can make decisions and perform actions without direct human guidance.

**Example**

A read-only code review assistant has lower autonomy than an Agent capable of modifying source code and executing terminal commands.

---

### Guard Rails

**Definition**

Technical or procedural safeguards that limit what an AI system is allowed to do.

**Example**

Requiring approval before modifying files or restricting access to specific directories.

---

# Try It Yourself

Choose a small development task.

For example:

> Investigate why this unit test fails.

Before asking the AI, write down the steps you would personally perform.

Then compare them with the Agent's approach.

Notice that successful Agents often behave surprisingly similarly to experienced developers.

---

# 🎉 Level Up!

You've reached an important milestone.

You now understand the distinction between:

- prompts,
- Skills,
- and Agents.

More importantly, you've learned that an Agent is not "more intelligent" than a Skill.

It simply coordinates multiple capabilities to solve larger problems.

You also understand why responsible autonomy requires thoughtful guard rails rather than unrestricted access.

### Next Level

An experienced developer doesn't solve every problem from scratch.

They remember previous projects, architectural decisions and recurring issues.

In the next chapter, you'll discover how AI systems can develop a similar capability through **Memory**, and why remembering the *right* things is often more important than remembering *everything*.