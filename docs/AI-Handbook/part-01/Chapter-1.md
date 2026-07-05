# Chapter 1 – What Is Artificial Intelligence?

*"Artificial Intelligence" is one of the most widely used—and most misunderstood—terms in software development today.*

Ask ten developers what AI is, and you'll likely receive ten different answers.

Some think of ChatGPT.

Others think of self-driving cars.

Some imagine robots.

Others think about GitHub Copilot.

All of these are related to Artificial Intelligence, but none of them *are* Artificial Intelligence.

To understand the modern AI ecosystem, we first need to understand where AI sits as a scientific discipline and how today's products fit into that larger picture.

---

# Artificial Intelligence Is an Umbrella Term

Artificial Intelligence (AI) is the broad field of computer science that aims to build systems capable of performing tasks that normally require human intelligence.

Those tasks include, among many others:

- understanding language
- recognizing images
- making decisions
- planning actions
- solving problems
- learning from experience
- playing games
- generating text
- writing software

Notice that none of these tasks mention ChatGPT, Copilot or Claude.

Those are merely products built upon techniques developed within the field of Artificial Intelligence.

One of the easiest mistakes to make when entering the AI world is assuming that AI began with ChatGPT.

It did not.

Researchers have been working on Artificial Intelligence since the 1950s. Modern Large Language Models are simply the latest milestone in a decades-long journey.

---

# A Helpful Analogy

The easiest way to think about AI is to compare it to another scientific discipline.

Consider medicine.

Medicine is an enormous field.

Nobody says they "work in medicine" and stops there.

Instead, medicine consists of many specializations.

```text
Medicine
│
├── Internal Medicine
├── Neurology
├── Cardiology
├── Oncology
└── Pediatrics
```

Each specialization contains further specializations.

```text
Medicine
│
└── Cardiology
     │
     ├── Electrophysiology
     ├── Heart Failure
     └── Cardiac Surgery
```

A heart surgeon is still working in medicine.

They are simply working in a very specific part of medicine.

Artificial Intelligence follows exactly the same pattern.

```text
Artificial Intelligence
│
├── Robotics
├── Computer Vision
├── Speech Processing
├── Planning
├── Machine Learning
└── ...
```

Just because someone works with Large Language Models does **not** mean they work with every area of AI.

Likewise, someone building autonomous robots may know very little about language models.

Understanding this hierarchy immediately makes many AI discussions less confusing.

---

# AI Is Bigger Than ChatGPT

When ChatGPT became publicly available, many people started using the words **AI** and **ChatGPT** interchangeably.

That is understandable, but technically incorrect.

It would be similar to saying:

> "I work in Microsoft."

when you actually mean

> "I use Microsoft Word."

One is an entire company.

The other is one product created by that company.

Likewise:

```text
Artificial Intelligence
        │
        └── Large Language Models
                │
                └── GPT Models
                        │
                        └── ChatGPT
```

ChatGPT is an application built around GPT models.

GPT models are one family of Large Language Models.

Large Language Models are one category within Artificial Intelligence.

Every level becomes more specific.

---

# The AI Hierarchy

Throughout this handbook we will repeatedly return to the same hierarchy.

Whenever you encounter a new technology, ask yourself:

> **Where does it fit?**

```text
Artificial Intelligence
│
├── Symbolic AI
│
├── Machine Learning
│   │
│   ├── Classical Machine Learning
│   │
│   └── Deep Learning
│        │
│        ├── Computer Vision
│        ├── Speech
│        └── Natural Language Processing
│              │
│              └── Large Language Models
│                   │
│                   ├── GPT
│                   ├── Claude
│                   ├── Qwen
│                   ├── Llama
│                   ├── Gemma
│                   └── Mistral
│
└── Robotics
```

Don't worry if several of these terms are unfamiliar.

We will explain each of them in later chapters.

For now, the important takeaway is simply this:

> AI is a hierarchy of increasingly specialized fields.

---

# Research Fields vs Products

Another common source of confusion is mixing up research fields, technologies and products.

For example:

| Research Field | Technology | Product |
|----------------|------------|----------|
| Artificial Intelligence | Large Language Model | ChatGPT |
| Artificial Intelligence | Large Language Model | Claude |
| Artificial Intelligence | Large Language Model | GitHub Copilot |
| Artificial Intelligence | Computer Vision | Image recognition software |

Notice something interesting.

ChatGPT and GitHub Copilot are **not** technologies.

They are products.

The underlying technology is the Large Language Model.

This distinction becomes increasingly important when you start building your own AI systems.

---

# Why Developers Should Care

As software developers, we rarely care about technology for its own sake.

We care because technology helps us solve problems.

The same is true for AI.

Your customers probably do not care whether your application uses a GPT model, a Qwen model or a Claude model.

They care that the application helps them accomplish their work more efficiently.

Likewise, when building your own local AI assistant, your goal is not to collect the latest AI tools.

Your goal is to build a system that genuinely improves your productivity.

That means choosing the right components—not necessarily the newest ones.

---

# Common Misconceptions

## "AI is ChatGPT."

No.

ChatGPT is an application that uses AI.

It is similar to saying that Microsoft Word *is* office software as a whole.

---

## "Every AI can do everything."

No.

Different AI systems specialize in different tasks.

Some excel at generating images.

Others recognize speech.

Others play chess.

Large Language Models specialize primarily in understanding and generating text.

---

## "If I learn ChatGPT, I understand AI."

Not yet.

Learning ChatGPT is comparable to learning how to use one IDE.

It is valuable, but it does not automatically explain compilers, operating systems or programming languages.

Similarly, using ChatGPT does not automatically explain how AI systems are built.

---

# Search Vocabulary

If you continue learning about AI online, you will frequently encounter these terms.

Don't worry about understanding all of them yet.

The goal is simply to recognize them.

| Term | Will be explained in |
|------|----------------------|
| Machine Learning | Chapter 2 |
| Deep Learning | Chapter 2 |
| Natural Language Processing (NLP) | Chapter 2 |
| Transformer | Chapter 3 |
| Foundation Model | Chapter 3 |
| Large Language Model (LLM) | Chapter 3 |
| Agent | Part II |
| RAG | Part III |
| MCP | Part III |

As you progress through the handbook, these terms will gradually move from "I've heard that word before" to "I know exactly where it fits."

---

# Developer's Decision

At this stage, you do **not** need to understand how neural networks work.

You do **not** need to know what a transformer is.

You do **not** need to know how models are trained.

Instead, focus on building one important mental model:

Artificial Intelligence is **not one technology**.

It is a collection of research fields and technologies.

Every product you will encounter throughout this handbook is built upon one or more of these technologies.

Knowing where something fits is often more valuable than knowing every implementation detail.

In the next chapter, we will zoom into one particular branch of Artificial Intelligence—the branch that made ChatGPT, Claude, GitHub Copilot and modern local language models possible.