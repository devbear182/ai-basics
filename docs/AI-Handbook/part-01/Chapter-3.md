# Chapter 3 – Foundation Models, Large Language Models and Multimodal Models

At this point we have travelled quite far down the AI hierarchy.

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
?
```

This is where many newcomers become confused.

Articles, conference talks and product pages suddenly begin using terms like:

- Foundation Model
- Large Language Model (LLM)
- Multimodal Model
- GPT
- Claude
- Gemini
- Qwen

Often without explaining how they relate.

In this chapter we will complete the hierarchy and build one of the most important mental models in the entire handbook.

---

# The Problem with the Word "Model"

One word appears everywhere in modern AI:

> **Model**

People say things like:

- "Download this model."
- "Switch to another model."
- "This model is smarter."
- "The model has 70 billion parameters."

But what exactly is a model?

A **model** is a piece of software that has learned statistical patterns from training data and can later apply those patterns to new input.

You can think of it as the result of a long training process.

During training, enormous amounts of computing power are used to gradually adjust billions of internal parameters.

Once training is complete, the resulting model can be copied and used by millions of users.

This is an important distinction.

When you download Qwen through Ollama, you are **not training AI**.

You are downloading an already trained model and asking it to perform **inference**, which simply means using the model to generate answers.

---

## Gaming Analogy

Imagine a professional gamer who has spent 10,000 hours mastering a game.

Training is those 10,000 hours.

Playing a new match is inference.

When you use an AI model, you are interacting with the equivalent of the experienced player—not watching them learn from scratch.

---

# Foundation Models

## Where do they fit?

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
Foundation Models
```

A **Foundation Model** is a large pretrained AI model that serves as the starting point for many different applications.

The word **foundation** is used because these models provide a foundation upon which other capabilities can be built.

Instead of training one model for translation, another for summarization and another for programming, a foundation model learns broad knowledge first.

Later it can be adapted for many different purposes.

Examples include:

- answering questions
- writing software
- summarizing documents
- translating languages
- generating reports
- assisting with research

This idea fundamentally changed how AI systems are developed.

---

## Software Engineering Analogy

Imagine Microsoft released a version of .NET that already contained:

- networking
- JSON serialization
- dependency injection
- logging
- authentication
- configuration

Every application would start from that shared foundation instead of rebuilding everything from scratch.

Foundation Models play a similar role in AI.

They provide an enormous amount of general capability before any application-specific customization takes place.

---

# Large Language Models (LLMs)

## Where do they fit?

```text
Foundation Models
        │
        ▼
Large Language Models
```

A **Large Language Model (LLM)** is a Foundation Model whose primary purpose is understanding and generating language.

The word **Large** refers to both:

- the amount of training data
- the number of parameters inside the model

The word **Language** refers to natural language, such as English or German.

The word **Model** refers to the trained neural network itself.

Together they describe a model that has learned statistical relationships within language on a massive scale.

---

## More Than Just Human Language

Despite the name, Large Language Models do far more than write sentences.

Modern programming languages are themselves a form of language.

Consider this C# method.

```csharp
public int Add(int a, int b)
{
    return a + b;
}
```

To us, this is code.

To an LLM, it is another structured language.

During training, the model learned patterns from both natural languages and programming languages.

That is why the same model can:

- explain a legal document
- summarize a meeting
- translate German
- write SQL
- generate C#
- review code
- explain an exception

These are all language-related tasks.

---

# Are LLMs Intelligent?

This question appears frequently.

The honest answer is:

> It depends on what you mean by "intelligent."

An LLM does not possess human consciousness.

It does not have beliefs.

It does not have emotions.

It does not "know" things in the way humans do.

Instead, it predicts the most likely next token based on everything it has seen so far.

Surprisingly, this relatively simple objective leads to remarkably sophisticated behaviour.

As models become larger and training improves, capabilities emerge that were never explicitly programmed.

Researchers call these **emergent capabilities**.

For example, nobody manually programmed GPT or Qwen with thousands of software design rules.

Instead, these capabilities emerged from learning patterns across enormous datasets.

---

# Multimodal Models

Not every Foundation Model is limited to text.

Some models understand multiple types of information simultaneously.

These are called **Multimodal Models**.

The prefix **multi-** simply means "more than one."

The word **modality** refers to a type of information.

Examples include:

- text
- images
- audio
- video
- documents
- diagrams

A multimodal model can combine several of these inputs when solving a problem.

---

## Examples

Suppose you upload a screenshot of a compiler error.

A text-only model cannot directly understand the image.

A multimodal model can.

You might ask:

> "Why does this code fail to compile?"

The model first understands the image.

It then understands the code visible within the image.

Finally, it generates a textual explanation.

Likewise, you could upload:

- a UML diagram
- a whiteboard photo
- a flowchart
- a PDF specification

and discuss them naturally.

---

## Important Observation

Every Large Language Model is **not** automatically multimodal.

Likewise, not every multimodal model is primarily designed for language.

The hierarchy therefore looks like this.

```text
Foundation Models
│
├── Large Language Models
│     │
│     ├── GPT
│     ├── Claude
│     ├── Qwen
│     ├── Llama
│     └── Mistral
│
├── Vision Models
│
├── Audio Models
│
└── Multimodal Models
      │
      ├── GPT
      ├── Claude
      └── Gemini
```

Notice something interesting.

Some product families appear in more than one branch.

That is because companies often provide multiple variants of their models.

For example, one version may be language-only while another also understands images.

---

# Where Does Qwen 2.5 Fit?

Let's revisit the question that inspired this handbook.

When you asked your local Qwen model what it was, it described itself as an NLP model.

That answer was technically correct—but incomplete.

We can now place it precisely within the hierarchy.

```text
Artificial Intelligence
│
└── Machine Learning
     │
     └── Deep Learning
          │
          └── Natural Language Processing
               │
               └── Foundation Model
                    │
                    └── Large Language Model
                         │
                         └── Transformer
                              │
                              └── Qwen 2.5
```

Each level becomes increasingly specific.

Saying

> "Qwen is an NLP model."

is similar to saying

> "I'm a doctor."

Correct.

But much less informative than saying

> "I'm a cardiac surgeon."

Likewise,

> "Qwen is a transformer-based Large Language Model."

provides much more useful information.

---

# Why This Matters

Many online discussions become confusing because people describe the same system at different levels.

Consider these statements.

> GPT is an AI.

True.

> GPT is a Foundation Model.

Also true.

> GPT is an LLM.

Also true.

> GPT is a Transformer.

Again true.

None of these statements contradict each other.

They simply describe different levels within the hierarchy.

---

# Common Misconceptions

## "Every Foundation Model is an LLM."

No.

LLMs are one category of Foundation Models.

Other Foundation Models specialize in images, speech or multiple modalities.

---

## "Every LLM understands images."

No.

Many LLMs process only text.

Image understanding requires additional capabilities.

---

## "ChatGPT is the model."

Not quite.

ChatGPT is an application.

The underlying GPT model is the model.

This distinction becomes extremely important when we begin building our own local AI systems.

---

# Search Vocabulary

After this chapter you should recognize the following terms.

| Term | Practical meaning |
|------|-------------------|
| Model | A trained neural network used to perform inference. |
| Foundation Model | Broadly trained model used as the basis for many tasks. |
| LLM | Foundation Model specialized in language. |
| Multimodal Model | Foundation Model that understands multiple data types. |
| Inference | Running a trained model to produce output. |
| Parameters | Internal values learned during training. |

Don't worry if "parameters" still sounds abstract.

We'll return to that concept when we discuss model sizes such as **7B**, **14B** and **70B**.

---

# Developer's Decision

At this point you know enough to interpret most AI product descriptions.

If somebody says:

> "Run a local 7B LLM in Ollama."

you now understand that they are referring to:

- a pretrained model,
- specialized for language,
- based on the Transformer architecture,
- executed locally on your own hardware.

You still don't know **how** these models are delivered to your computer or how applications such as ChatGPT, Open WebUI and GitHub Copilot interact with them.

That is exactly where we are headed next.

The next chapter leaves AI theory behind for a moment and introduces the practical software architecture behind modern AI assistants.