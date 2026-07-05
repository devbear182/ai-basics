# Chapter 7 – Tokens: The Language AI Actually Reads

One of the first technical terms you'll encounter when working with AI is **token**.

At first glance, the concept seems unnecessarily complicated.

After all, humans read words.

Why can't AI simply read words as well?

The answer is that computers don't naturally understand words.

They understand numbers.

Before a model can process your prompt, the text must first be converted into a numerical representation.

This conversion happens automatically every time you interact with an AI model.

Understanding tokens will help explain several seemingly unrelated topics:

- why models have context limits
- why APIs often charge "per token"
- why some prompts are slower than others
- why programming languages work well with LLMs
- why a "128k context window" does **not** mean 128,000 words

---

# What Is a Token?

A **token** is the smallest unit of text processed by a language model.

Many newcomers assume that a token is simply a word.

Sometimes it is.

Often it isn't.

For example, the sentence

> I love software development.

might be broken into tokens similar to:

```text
"I"

" love"

" software"

" development"

"."
```

Notice that spaces and punctuation may become part of individual tokens.

Now consider a longer word.

```text
internationalization
```

This might become several tokens.

Likewise, a very common short word like:

```text
the
```

may be represented by a single token.

The exact tokenization depends on the model.

Different model families may split the same text differently.

Fortunately, you almost never need to think about this during everyday use.

---

# Why Not Use Words?

Imagine creating a dictionary containing every possible word in every language.

Now consider:

- technical terminology
- programming languages
- variable names
- company names
- product names
- newly invented words

The list would never stop growing.

Instead, modern language models work with smaller building blocks that can be combined into almost any text.

This makes the system more flexible and allows it to understand previously unseen words by breaking them into familiar pieces.

---

# Programming Languages Are Languages Too

One reason LLMs perform surprisingly well with source code is that programming languages can also be represented as tokens.

For example:

```csharp
public int Add(int a, int b)
{
    return a + b;
}
```

To us, this is C#.

To the model, it becomes a sequence of tokens representing keywords, identifiers, punctuation and operators.

The model doesn't think:

> "This is a function."

Instead, it processes a long sequence of numerical representations.

Through training, it learns that certain sequences frequently appear together.

Eventually, these statistical relationships become powerful enough to generate syntactically correct code.

---

# Tokenization

The process of converting text into tokens is called **tokenization**.

Every prompt follows roughly this journey.

```text
Your Prompt
     │
     ▼
Tokenizer
     │
     ▼
Tokens
     │
     ▼
Numbers
     │
     ▼
AI Model
```

Notice that the model never receives your original text directly.

It receives numbers representing tokens.

The reverse happens when the model responds.

```text
Numbers
     │
     ▼
Tokens
     │
     ▼
Tokenizer
     │
     ▼
Text
```

This entire process happens in milliseconds.

---

# Tokens and Context Windows

In the previous chapter we learned about context windows.

A context window is measured in **tokens**, not words.

Suppose a model supports a context window of 128,000 tokens.

This does **not** mean:

- 128,000 words
- 128,000 characters
- 128,000 lines of code

It means exactly what it says.

The model can process approximately 128,000 tokens.

Depending on the type of content, that may correspond to more or fewer words.

For practical purposes, you can simply remember:

> Tokens are the unit used to measure how much information a model can process.

---

# Why APIs Charge Per Token

If you've looked at commercial AI pricing, you've probably seen something like:

> $X per million input tokens

> $Y per million output tokens

At first this seems strange.

Why not charge per request?

Imagine two users.

User A asks:

> "Translate this sentence."

User B uploads:

- a 400-page PDF
- three source code repositories
- a UML diagram
- dozens of questions

Clearly these requests require vastly different amounts of computation.

Charging by token reflects the amount of information the model actually processes.

---

# Input Tokens and Output Tokens

Every AI request has two sides.

## Input tokens

Everything sent **to** the model.

For example:

- your prompt
- previous conversation
- uploaded documents
- system instructions
- tool results

## Output tokens

Everything generated **by** the model.

The longer the response, the more output tokens are produced.

Many commercial services price these separately because generating output often requires additional computation.

---

# Why Long Conversations Become Slower

Suppose you've been chatting with an AI for an hour.

Each new message may include much of the earlier conversation as context.

Instead of processing:

> "How do I fix this bug?"

the model may now process:

- the original prompt
- twenty previous questions
- twenty previous answers
- uploaded files
- tool output

The amount of input grows over time.

More input usually means:

- more memory
- more computation
- longer response times

This is another reason applications sometimes summarize older parts of a conversation.

---

# Tokens Are Not Memory

People often say:

> "The model remembered that."

What usually happened is simpler.

The information was still present in the context window.

If it disappears from the context window, the model typically stops using it.

A useful analogy is sticky notes on your monitor.

As long as the note remains visible, you can refer to it.

Once it is removed, you no longer have immediate access to the information.

Tokens determine how many "sticky notes" the model can keep in front of it at once.

---

# Do I Need to Count Tokens?

For most developers, the answer is:

No.

Modern AI applications automatically handle tokenization.

You rarely need to think about individual tokens.

However, it helps to understand tokens when:

- selecting models
- estimating API costs
- working with very large documents
- debugging context-related issues
- comparing model capabilities

Knowing the concept is enough for now.

Precise token counting can wait until you begin building production AI applications.

---

# A Small Experiment

Imagine asking an AI:

> "Summarize this book."

Now compare it with:

> "Summarize this paragraph."

The second request feels obviously smaller.

Internally, the difference is simply that one request contains far fewer tokens than the other.

This observation explains many practical limitations of today's AI systems.

---


> ⚠️ Important note for developers:
>
> Context windows and tokens are not just theoretical limitations.
> They directly affect how you design workflows with AI.
>
> The key question is not only "what is context?" but:
>
> > "How do I actively manage context over time in a way that stays efficient?"
>
> This includes patterns like:
> - summarizing ongoing conversations
> - extracting persistent knowledge from temporary context
> - splitting large tasks into smaller context windows
> - re-feeding structured state back into the model
> - externalizing memory into files, repositories or tools
>
> These techniques will be covered in detail in **Part II (Building AI Systems)** under "Context Engineering & Memory Management".

---

---

# Search Vocabulary

| Term | Meaning |
|------|---------|
| Token | Smallest unit of text processed by a language model. |
| Tokenization | Converting text into tokens. |
| Input Tokens | Tokens sent to the model. |
| Output Tokens | Tokens generated by the model. |
| Context Window | Maximum number of tokens considered in one request. |

When reading documentation, you'll often see context windows described as **8k**, **32k**, **128k**, or even larger values.

The **k** stands for **thousand tokens**, not thousand words.

---

# Developer's Decision

At this point, you do **not** need to worry about manually counting tokens.

Instead, remember these practical rules:

- A context window is measured in tokens.
- Every prompt and every response consumes tokens.
- Larger documents require more tokens.
- Longer conversations consume more tokens.
- Commercial AI services often charge based on token usage.

Whenever you encounter discussions about context windows, pricing, or performance, you now know that **tokens are the common unit connecting all three**.

The next chapter answers another question that almost every developer asks when starting with local AI:

> **What does "7B", "14B" or "70B" actually mean, and why are there so many versions of the same model?**