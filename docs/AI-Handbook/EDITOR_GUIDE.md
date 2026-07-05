# AI Basics Handbook – Editor Guide

## Purpose

This document serves as the long-term editorial guide for the handbook.

It is intended for both human editors and AI assistants contributing to the project.

The goal is to ensure consistency across all chapters, even when they are written in different sessions or by different contributors.

---

# Target Audience

Primary audience:

- Windows-focused junior software developers
- Some professional software development experience
- Little or no AI experience
- Interested in adopting AI for daily software development

Typical reader questions:

- What do all these AI terms mean?
- How do ChatGPT, Copilot and Ollama relate?
- How can I build my own local AI assistant?
- Which concepts do I need today?
- Which topics can wait until later?

The reader is assumed to have:

- basic programming knowledge
- basic Git knowledge
- basic command line experience

The reader is **not** assumed to know:

- machine learning
- statistics
- neural networks
- data science
- mathematics behind transformers

---

# Teaching Philosophy

The handbook follows one central principle:

> Build understanding before building systems.

Every chapter should answer three questions:

1. What is it?
2. Why does it exist?
3. Where does it fit?

Only afterwards explain:

4. How does it work?

Whenever possible, postpone mathematical details until they become practically relevant.

---

# Learning Philosophy

Readers should gain enough understanding to:

- recognize terminology
- search for additional information
- evaluate AI products
- make informed architectural decisions

The handbook is **not** intended to replace academic textbooks.

---

# Writing Style

Prefer:

- clear English
- short paragraphs
- active voice
- practical explanations
- software engineering analogies

Avoid:

- unnecessary buzzwords
- unexplained jargon
- mathematical notation
- excessive marketing language

---

# Recurring Chapter Structure

Whenever appropriate, chapters follow this structure:

1. Motivation
2. Definition
3. Mental Model
4. Software Engineering Analogy
5. Practical Examples
6. Search Vocabulary
7. Developer's Decision

Not every chapter must contain every section.

---

# Recurring Themes

The following ideas should appear throughout the handbook.

## "Where does it fit?"

Every concept should be positioned inside the larger AI ecosystem.

---

## Build Mental Models

The goal is understanding.

Readers should leave a chapter thinking:

> "Now I understand why this exists."

---

## Build Vocabulary

Every important technical term should be introduced before being used extensively.

Definitions should be sufficient for productive web searches.

---

## Progressive Learning

Avoid deep dives before they become useful.

Example:

Explain quantization.

Do **not** explain quantization mathematics.

---

## Engineering Perspective

Always explain concepts from the perspective of someone building software.

Not from the perspective of an AI researcher.

---

# Diagram Philosophy

Prefer simple ASCII diagrams.

Example:

```text
User
 │
 ▼
Application
 │
 ▼
Model
```

Diagrams should explain relationships rather than implementation details.

---

# Analogies

Prefer analogies from:

- software engineering
- Git
- databases
- operating systems
- computer networking
- software architecture

Occasionally use:

- whiteboards
- libraries
- offices
- meetings

Avoid analogies requiring specialist knowledge outside software engineering.

---

# Icons

Use icons very sparingly.

Good uses:

💡 Idea

⚠️ Warning

Avoid decorative emoji.

---

# Terminology

Prefer consistent terminology throughout the handbook.

Example:

- Model
- Runtime
- Application
- Platform

Avoid switching between synonyms unless explaining them.

---

# End-of-Chapter Rule

Whenever possible, end a chapter by connecting it to the next one.

Readers should naturally think:

> "Now I want to know what comes next."

The handbook should feel like one continuous journey rather than isolated articles.