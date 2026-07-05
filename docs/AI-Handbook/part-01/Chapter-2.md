# Chapter 2 – From Artificial Intelligence to Large Language Models

In the previous chapter we established that **Artificial Intelligence** is not a single technology but an umbrella term that covers many different research fields.

In this chapter we will gradually zoom in on the branch that ultimately leads to modern AI assistants such as ChatGPT, Claude and locally hosted models like Qwen.

One of the most common sources of confusion is that people use terms like *AI*, *Machine Learning*, *Deep Learning*, *NLP* and *LLM* almost interchangeably.

They are related—but they are **not** synonyms.

By the end of this chapter you should be able to confidently explain the relationship between them and know exactly where modern language models fit.

---

# Following the Branch

Think back to the medicine analogy.

Suppose someone says:

> "I'm a surgeon."

That already tells you something, but not very much.

Are they a brain surgeon?

An orthopedic surgeon?

A heart surgeon?

The deeper you travel down the hierarchy, the more specific the description becomes.

The same is true in AI.

```text
Artificial Intelligence
        │
        ▼
Machine Learning
        │
        ▼
Deep Learning
        │
        ▼
Natural Language Processing
        │
        ▼
Foundation Models
        │
        ▼
Large Language Models
        │
        ▼
GPT, Claude, Qwen, Llama...
```

Each level inherits everything above it while becoming increasingly specialized.

This tree is one of the most important diagrams in the entire handbook.

You will see it many times.

---

# Machine Learning

## Where does it fit?

```text
Artificial Intelligence
│
└── Machine Learning
```

Machine Learning (ML) is a branch of Artificial Intelligence in which computers learn patterns from data instead of following only explicitly programmed rules.

Traditional software behaves like this:

```csharp
if (temperature > 25)
{
    fan.Start();
}
```

Every rule is written by a developer.

Machine Learning approaches many problems differently.

Instead of writing every rule yourself, you provide examples.

The computer then discovers statistical patterns within those examples.

For instance, instead of writing thousands of rules describing spam emails, you train a model using thousands of emails already labeled as "spam" or "not spam."

The model learns the differences.

---

## Why was this such a breakthrough?

Some problems are simply too complicated to describe with rules.

Imagine writing software that recognizes cats in photographs.

Where would you begin?

You could write rules such as:

- two ears
- two eyes
- whiskers
- tail
- fur

But what about:

- different colors?
- different poses?
- partially hidden cats?
- sleeping cats?
- kittens?
- cartoons?

Very quickly the number of rules becomes enormous.

Machine Learning solved many of these problems by learning from examples instead of manually programmed rules.

---

## Do I need this now?

Yes—but only at a conceptual level.

As a software developer you probably won't train your own models anytime soon.

However, understanding that modern AI systems are **trained** rather than **explicitly programmed** explains many of their strengths and limitations.

---

# Deep Learning

## Where does it fit?

```text
Artificial Intelligence
│
└── Machine Learning
     │
     └── Deep Learning
```

Deep Learning is a specialized branch of Machine Learning based on large neural networks.

The word **deep** refers to the many layers within these neural networks.

You do **not** need to understand the mathematics behind them.

Instead, think of Deep Learning as the technology that enabled dramatic improvements in areas such as:

- image recognition
- speech recognition
- language translation
- code generation
- conversational AI

Nearly every modern AI product you interact with today is powered by Deep Learning.

---

## Neural Networks

A **neural network** is a mathematical model inspired—very loosely—by the way biological neurons communicate in the brain.

The inspiration is historical rather than literal.

Modern neural networks do **not** simulate the human brain.

Instead, they consist of many interconnected mathematical units that gradually learn useful patterns from training data.

You can think of a neural network as a very large function whose internal parameters are adjusted during training.

Those parameters eventually encode useful knowledge about the data the model has seen.

Later chapters will explain what people mean when they say a model has "7 billion parameters."

---

## Why Developers Should Care

You are unlikely to build your own neural network.

You are very likely to use one.

Just as most .NET developers never implement their own garbage collector, most AI developers never train their own foundation model.

Instead, they build software on top of existing models.

---

# Natural Language Processing (NLP)

## Where does it fit?

```text
Artificial Intelligence
│
└── Machine Learning
     │
     └── Deep Learning
          │
          └── Natural Language Processing
```

Natural Language Processing (NLP) is the field concerned with enabling computers to understand, analyze and generate human language.

"Natural language" simply means the languages humans naturally speak or write, such as English, German, French or Japanese.

Programming languages like C# or Python are **not** considered natural languages.

---

## Before Large Language Models

Long before ChatGPT existed, NLP researchers were already building systems for tasks like:

- spell checking
- grammar correction
- machine translation
- speech transcription
- sentiment analysis
- keyword extraction
- document classification
- search engines

Each of these tasks often required its own specialized model.

If you wanted to solve ten different NLP problems, you frequently needed ten different AI systems.

---

## Then Everything Changed

Around 2017, researchers introduced a new neural network architecture called the **Transformer**.

It proved remarkably good at understanding relationships within language.

As models based on this architecture grew larger and were trained on increasingly massive datasets, they became capable of performing many different NLP tasks without needing a separate model for each one.

This was the beginning of the era of Large Language Models.

---

# Transformer

## Where does it fit?

```text
Deep Learning
        │
        ▼
Transformer Architecture
        │
        ▼
Large Language Models
```

A **Transformer** is a neural network architecture introduced in 2017 that forms the basis of nearly every modern Large Language Model.

Its key innovation is a mechanism called **attention**, which allows the model to determine which words or tokens are most relevant to one another when processing text.

Unlike earlier language models that processed text strictly from left to right, transformers can consider relationships across an entire sequence at once.

This dramatically improved both language understanding and training efficiency.

---

## Gaming Analogy

Imagine playing an open-world role-playing game.

Older NPCs might react only to the last thing you said.

A transformer-based model behaves more like an experienced dungeon master.

Instead of remembering only your previous sentence, it constantly considers the entire recent conversation when deciding how to respond.

It doesn't just ask:

> "What was the previous word?"

It asks:

> "Considering everything I've seen so far, what comes next?"

That difference turned out to be revolutionary.

---

## Do I need to understand attention?

Not today.

It is enough to remember:

> Transformers replaced older language model architectures because they understand context much more effectively.

If, at some point, you become interested in training your own models or reading AI research papers, you can return for a deeper understanding.

---

# Foundation Models

The next step in our hierarchy introduces another term that is often used incorrectly.

A **Foundation Model** is a very large AI model trained on enormous amounts of general-purpose data.

Instead of learning one specific task, it learns broad patterns that can later be applied to many different problems.

Imagine hiring a new graduate software developer.

On their first day they don't know your company's products.

However, they already understand:

- programming
- algorithms
- source control
- debugging
- testing

They possess a strong foundation of general knowledge.

Later they learn your company's business domain.

Foundation Models work in a very similar way.

They first acquire broad, general knowledge.

Later they become specialized through prompting, fine-tuning, additional tools or external knowledge sources.

---

# Search Vocabulary

As you continue reading AI documentation, you will frequently encounter the following terms together:

- AI
- Machine Learning (ML)
- Deep Learning (DL)
- NLP
- Transformer
- Foundation Model
- Large Language Model (LLM)

Many articles assume these terms are interchangeable.

You now know they represent different levels of the same hierarchy.

---

# Developer's Decision

You have now reached an important milestone.

You can confidently explain that:

- Machine Learning is a branch of AI.
- Deep Learning is a branch of Machine Learning.
- NLP is one application area of Deep Learning.
- Transformers are the architecture behind modern language models.
- Foundation Models are broadly trained models that can be adapted to many tasks.

There is one final piece missing before we can properly place ChatGPT, Claude, Qwen and Llama into this hierarchy.

That piece is the **Large Language Model (LLM)**, which is the subject of the next chapter.