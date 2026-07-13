# Chapter 22 – Model Context Protocol (MCP): A Common Language for AI Tools

In the previous chapters, you've gradually assembled an increasingly capable AI assistant.

It can:

- understand your instructions,
- access your project,
- remember important information,
- retrieve documentation,
- search semantically using embeddings,
- coordinate work through Agents.

One important question remains.

How does the AI actually communicate with the outside world?

For example:

- How can it query GitHub?
- How can it read Jira work items?
- How can it inspect Azure DevOps?
- How can it search your local files?
- How can it call your own REST APIs?

Until recently, every AI application solved this problem differently.

Today, an increasingly popular solution is the **Model Context Protocol (MCP)**.

---

# The Problem

Imagine buying a new gaming keyboard.

One game expects:

```
Jump = Space
```

Another expects:

```
Jump = J
```

Another requires:

```
Jump = Ctrl + Shift
```

Every game invents its own control scheme.

Eventually, players become frustrated.

Software developers experience exactly the same problem.

Suppose five AI applications all want to communicate with GitHub.

Without a common standard, every application needs its own GitHub integration.

```
ChatGPT

↓

GitHub Integration A
```

```
Claude

↓

GitHub Integration B
```

```
Open WebUI

↓

GitHub Integration C
```

```
Continue

↓

GitHub Integration D
```

```
Cline

↓

GitHub Integration E
```

The same functionality is implemented repeatedly.

That isn't a good engineering solution.

---

# A Software Engineering Analogy

As developers, we've solved this problem many times before.

Think about databases.

Years ago, every application talked to every database differently.

Then standards emerged.

Think about:

- ODBC
- JDBC
- ADO.NET

Applications no longer needed to know every implementation detail.

Instead, they communicated through a common interface.

MCP follows exactly the same philosophy.

Instead of standardising databases, it standardises **AI tools**.

---

# What Is MCP?

The **Model Context Protocol** is an open protocol that allows AI applications to discover and use external capabilities through a common interface.

Notice something subtle.

MCP is **not**:

- a language model,
- an Agent,
- a runtime,
- a chat application.

It is a communication standard.

Just as HTTP defines how web browsers communicate with web servers, MCP defines how AI applications communicate with external tools.

---

# The Architecture

A simplified view looks like this.

```
Developer

↓

AI Application

↓

MCP Client

↓

MCP Server

↓

External Tool
```

The AI itself never directly communicates with GitHub, SQL Server or Jira.

Instead, it asks an MCP client to call the appropriate MCP server.

That server performs the actual work.

---

# What Is an MCP Server?

An MCP server exposes one or more capabilities.

For example:

```
GitHub MCP Server

↓

Read repositories

Create issues

Review pull requests
```

Or:

```
File System MCP Server

↓

Read files

Search folders

List directories
```

Or:

```
SQL Server MCP Server

↓

Execute queries

Read schema

Inspect tables
```

Every server advertises the capabilities it provides.

The AI can discover them dynamically.

---

# Why This Is Such a Big Deal

Without MCP, every AI application must implement every integration itself.

With MCP:

```
GitHub MCP Server

↓

ChatGPT

Claude

Continue

Open WebUI

Cline

...and many others
```

One integration.

Many AI applications.

This greatly reduces duplicated engineering effort.

---

# Think of USB

Perhaps the best analogy is USB.

Imagine if every printer required:

- its own connector,
- its own cable,
- its own driver,
- its own protocol.

Instead, USB standardised communication.

Manufacturers build USB devices.

Operating systems know how to communicate through USB.

Applications simply use the operating system.

MCP aims to become something similar for AI tools.

Instead of learning fifty different integration mechanisms, AI applications can communicate through one common protocol.

---

# A Practical Example

Suppose you ask:

> Which pull requests assigned to me are waiting for review?

An MCP-enabled workflow might look like this:

```
Developer

↓

AI

↓

GitHub MCP Server

↓

GitHub API

↓

Pull Requests

↓

AI summarises results
```

The AI didn't know anything about GitHub beforehand.

It simply knew that a tool capable of answering your question existed.

---

# Your Own Applications Can Participate

One particularly exciting aspect of MCP is that it isn't limited to commercial services.

Imagine your company has an internal system called:

```
Customer Portal
```

Without MCP, every AI application would require its own custom integration.

With MCP, you can build:

```
Customer Portal MCP Server
```

Suddenly, any compatible AI application can interact with your system.

This is one reason why many companies are paying close attention to MCP.

---

# Does the AI Automatically Trust Every MCP Server?

Absolutely not.

Remember our earlier discussion about guard rails.

Connecting an MCP server simply makes capabilities available.

It does **not** mean the AI should use them without restrictions.

Permissions still matter.

For example:

- read customer information,
- create work items,
- delete repositories,
- execute shell commands,

should not all receive the same level of trust.

MCP standardises communication—not security policy.

You still decide what the AI is allowed to do.

---

# MCP Is About Interoperability

One important misconception is:

> "MCP makes AI smarter."

It doesn't.

Instead, it makes AI systems **more connected**.

The model still performs the reasoning.

MCP simply expands the set of tools the model can access.

Think back to our earlier toolbox analogy.

The carpenter hasn't become more skilled.

They simply have access to more tools.

---

# Engineering Note

If you've worked with software architecture before, you'll notice a familiar pattern.

```
Interface

↓

Implementation
```

Your application depends on the interface.

Different implementations can be swapped in later.

MCP applies exactly the same principle.

The AI interacts with capabilities through a standard protocol rather than depending on proprietary integrations.

This makes AI ecosystems significantly more modular.

---

# Behind the Scenes

MCP is intentionally similar to many protocols developers already know.

The language model doesn't communicate directly with GitHub, SQL Server or your own applications.

Instead, it discovers available capabilities from one or more MCP servers and requests their execution through a standard protocol.

This separation keeps AI applications independent from the specific tools they use.

---

# Looking Ahead

Your AI assistant can now interact with many external systems.

But another question naturally follows.

How should you **design** your own AI capabilities?

When should something become:

- an instruction,
- a Skill,
- an Agent,
- an MCP server,
- or ordinary software?

Answering those questions well is one of the biggest differences between experimenting with AI and engineering reliable AI systems.

In the next chapter, we'll step back from the individual technologies and look at the architectural design principles that help you build AI systems that remain understandable, maintainable and secure as they grow.

---

# Search Vocabulary

### Model Context Protocol (MCP)

**Definition**

An open protocol that standardises how AI applications discover and communicate with external tools and services.

**Compare to**

Similar in spirit to HTTP for web communication or ODBC/JDBC for database access.

**Example**

Using the same GitHub MCP server from different AI applications without writing separate integrations for each.

---

### MCP Server

**Definition**

A program that exposes one or more capabilities through the Model Context Protocol.

**Example**

An MCP server that allows AI assistants to search repositories, execute database queries or access internal business systems.

---

### MCP Client

**Definition**

The component inside an AI application that communicates with MCP servers on behalf of the language model.

**Example**

A Visual Studio Code extension connecting to a local file-system MCP server.

---

### Interoperability

**Definition**

The ability of different systems to work together using shared standards and protocols.

**Compare to**

Just as USB allows many devices to connect to many computers, MCP enables many AI applications to communicate with many external tools.

**Example**

Switching from one AI application to another while continuing to use the same MCP servers.

---

# Try It Yourself

Think about one application you use every day.

Examples:

- Azure DevOps
- Jira
- Outlook
- SQL Server
- GitHub
- your company's internal REST API

Now ask yourself:

> If this application exposed an MCP server, which capabilities would I actually want my AI assistant to have?

You'll probably notice that you don't want "full access."

Instead, you'll naturally begin thinking in terms of focused capabilities such as:

- search work items,
- read documentation,
- list pull requests,
- execute approved SQL queries.

Congratulations—you've just started designing AI integrations the way an AI engineer would.

---

# 🎉 Level Up!

You've just learned one of the newest and most influential concepts in the AI ecosystem.

You now understand:

- why AI applications need a common protocol for tools,
- how MCP separates interfaces from implementations,
- why one MCP server can serve many AI applications,
- and why protocols improve flexibility without making models themselves more intelligent.

Perhaps the biggest insight is this:

**The future of AI isn't one enormous application that does everything.**

It's an ecosystem of specialised components that communicate through shared standards—just like modern software systems already do.

### Next Level

So far, you've learned *what* the major building blocks are.

Next, you'll learn **how to combine them effectively**.

We'll begin looking at practical AI architecture patterns and answer one of the most common developer questions:

> *"When should I solve this with prompts—and when should I write actual code instead?"*

This is where AI engineering truly begins.