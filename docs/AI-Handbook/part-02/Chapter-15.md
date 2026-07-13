# Chapter 15 – Giving Your AI Access to Your Project

In the previous chapter, you learned how to make your AI behave more consistently by separating stable instructions from project documentation.

However, there is still an obvious limitation.

Even if your AI knows your preferred coding style, it still cannot answer questions like:

> "Where is the implementation of `OrderService`?"

or

> "Which classes call this method?"

or

> "Does another project already solve this problem?"

Why?

Because the AI still cannot see your project.

Let's fix that.

---

# The Problem

Imagine calling a colleague and asking:

> "Can you review my implementation?"

They answer:

> "Sure, send me the code."

Instead you reply:

> "I won't send it. Just imagine it."

Obviously that won't work.

The same is true for AI.

An AI can only reason about information it actually receives.

No matter how intelligent the model is, it cannot inspect files that have never been shared with it.

---

# Two Ways to Give AI Context

There are two fundamentally different approaches.

## Option 1 – Manual Context

You copy and paste:

- source code
- log files
- configuration
- documentation

into the chat.

```
Developer
        │
        ▼
Copy & Paste
        │
        ▼
AI
```

This is simple and often sufficient for small tasks.

Examples include:

- reviewing a single class
- explaining an exception
- writing unit tests
- documenting a method

Many developers use AI exactly this way.

---

## Option 2 – Tool-Assisted Context

Instead of manually copying files, the AI can use tools to access them directly.

```
Developer
        │
        ▼
AI
        │
        ▼
Read File Tool
        │
        ▼
Repository
```

Instead of asking you to paste a file, the AI can retrieve the information itself.

This makes working with larger projects much more practical.

---

# Why This Matters

Suppose you ask:

> Explain how orders are processed.

If you only provide one file, the AI sees only one small piece of the puzzle.

A human developer would probably open several files:

- the controller,
- the service,
- the repository,
- related models,
- configuration.

An AI benefits from exactly the same approach.

The more relevant context it has, the better it can reason about your project.

---

# Reading Is Different from Writing

Giving an AI access to files does **not** automatically mean giving it permission to modify them.

These are two separate capabilities.

Think of Windows Explorer.

Having permission to open a document does not necessarily allow you to edit or delete it.

The same principle applies to AI.

Reading source code is considerably less risky than automatically modifying it.

Whenever possible, start with read-only access.

---

# The Principle of Least Privilege

One of the oldest principles in computer security is:

> Give only the permissions that are actually required.

Suppose you want your AI to summarize log files.

Does it need permission to:

- delete files?
- rename directories?
- push commits?
- access production secrets?

Of course not.

It only needs permission to read the log files.

This principle is known as the **Principle of Least Privilege**, and it applies just as much to AI systems as it does to users and services.

---

# A Practical Example

Imagine you're working on a bug report.

Instead of manually collecting several files, you could ask:

> Explain how an order moves through the system.

A tool-enabled AI might automatically inspect:

```
OrderController.cs

↓

OrderService.cs

↓

OrderRepository.cs

↓

Order.cs

↓

appsettings.json
```

It can now explain the complete workflow instead of only discussing a single file.

Notice that the AI didn't become smarter.

It simply received better context.

---

# Different Levels of Access

As your AI assistant becomes more capable, you'll gradually grant additional permissions.

A typical progression looks like this:

```
No access

↓

Read files

↓

Search repository

↓

Compare files

↓

Suggest changes

↓

Modify files

↓

Run commands

↓

Create commits
```

You do **not** need all of these capabilities on day one.

In fact, you usually shouldn't.

Start with the smallest set of permissions that allows you to accomplish your current task.

You can always add more later.

---

# Local AI vs Cloud AI

One advantage of running AI locally is that you decide what the model can access.

For example, you might allow access only to:

- a single repository,
- one documentation folder,
- a temporary workspace.

Cloud-based AI services often provide similar capabilities, but you should always understand:

- what data is being sent,
- where it is processed,
- how long it is stored,
- and who can access it.

For many organizations, these questions are just as important as the quality of the AI's answers.

---

# Common Beginner Mistake

After successfully giving an AI access to a repository, many developers become tempted to grant every available permission.

For example:

- unrestricted file access,
- terminal access,
- automatic commits,
- access to multiple repositories.

This is rarely necessary.

Instead, follow the same security mindset you would apply when creating a service account.

Grant permissions gradually as genuine needs arise.

---

# Engineering Note

Experienced software engineers often talk about building trust.

The same applies to AI.

Don't start by asking your AI to modify hundreds of files automatically.

Start by letting it:

- explain,
- summarize,
- search,
- compare,
- review.

Once you've gained confidence in its behaviour, you can gradually allow more powerful capabilities.

Trust should be earned—not assumed.

---

# Looking Ahead

Your AI can now understand much larger parts of your project.

But interacting through a browser still has one inconvenience.

Every time you want to ask about code, you have to leave your development environment.

Wouldn't it be better if the AI were available directly inside your IDE?

In the next chapter, you'll integrate your local AI into Visual Studio Code and discover why tools such as Continue and GitHub Copilot feel so natural during everyday development.

---

# Behind the Scenes

When you ask an AI to explain a class, the model itself cannot open files.

Instead, the AI application calls a **tool** on the model's behalf.

A simplified workflow looks like this:

```
Developer

↓

Language Model

↓

Read File Tool

↓

Repository

↓

Language Model

↓

Answer
```

The model decides *what* information it needs.

The tool retrieves it.

The model then reasons over the returned information.

---

# Search Vocabulary

### Tool

**Definition**

A capability that allows an AI model to interact with external systems, such as reading files, searching repositories or executing commands.

**Compare to**

Similar to calling an API from an application. The model itself cannot perform the action—it requests that a tool performs it.

**Example**

A "Read File" tool allows the AI to inspect a source file before answering a question about it.

---

### Principle of Least Privilege

**Definition**

A security principle stating that users, services and applications should receive only the permissions necessary to perform their current task.

**Example**

An AI assistant that only reviews source code should receive read-only access instead of full write access to the repository.

---

### Context

**Definition**

The information available to the AI while generating a response.

**Compare to**

Similar to the documents and source code a developer has open while working on a task.

**Example**

Repository files, project documentation and the current conversation together form the AI's context.

---

# Try It Yourself

Open a repository that contains several related classes.

Instead of selecting only one file, ask:

> Explain how this feature works from end to end.

Observe which additional files your AI retrieves.

Then compare this with manually pasting a single source file.

Notice how dramatically the explanation improves when the AI has access to broader project context.

---

# 🎉 Level Up!

Your AI assistant has taken an important step forward.

It no longer depends entirely on manually pasted information.

You now understand:

- why AI needs access to project files,
- the difference between reading and writing,
- why permissions should be granted gradually,
- and how better context leads to better answers.

More importantly, you've learned that increasing an AI's usefulness often has less to do with changing the model and more to do with giving it the right information in a safe and controlled way.

### Next Level

In the next chapter, you'll move your AI even closer to your daily workflow by integrating it directly into your IDE.

Instead of switching between your editor and a browser, your AI will become another tool in your development environment—working alongside your debugger, terminal and source control.