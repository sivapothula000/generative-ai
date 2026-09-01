# Day 16/60 — Choosing the Right LLM & Understanding Model Evaluation

## Course Context

- **Course:** AI Core Track
- **Week:** Week 4 — LLM Showdown: Evaluating Models for Code Gen & Business Tasks
- **Focus:** Model selection, Chinchilla Scaling Law, AI benchmarks, and benchmark limitations

---

## 1. Choosing the Right LLM

The goal is **not** to find one universally "best" LLM.

The goal is to choose the **right model for the task at hand**.

### Start with the basics

When comparing LLMs, first look at:

- **Parameters**
- **Context length**
- **Pricing**
- **Training tokens**

Then look at:

- **Benchmarks**
- **Leaderboards**
- **Money / cost**

---

## 2. Important LLM Features to Compare

### Model source

- **Open-source / open-weight**
- **Closed-source**

This affects how much control we have over the model, deployment, customization, and access.

### Model type

- **Chat models**
- **Reasoning models**
- **Hybrid models**

Different model types can be better suited to different workloads.

### Knowledge cutoff

The model's knowledge cutoff matters because it determines how recent its built-in knowledge can be.

### Parameters

Parameters are the learned values inside a model.

A larger number of parameters generally means a larger model, but **larger does not automatically mean better for every task**.

### Training tokens

The amount of training data/tokens is another important factor when evaluating a model.

### Context window

The context window determines how much information the model can process as context for a request.

---

## 3. Practical / Business Factors

Model quality is only one part of model selection.

Also compare:

- **Inference cost**
- **Training cost**
- **Overall business cost**
- **Time to market**
- **Rate limits**
- **Speed**
- **Latency**
- **License**

A model with excellent benchmark results may still be a poor choice if it is too expensive, too slow, difficult to deploy, or has an unsuitable license.

### Simple model-selection idea

```text
Task
 ↓
Required capability
 ↓
Compare models
 ↓
Check benchmarks
 ↓
Check cost + latency + limits
 ↓
Check license / deployment requirements
 ↓
Choose the best fit
```

---

# 4. Chinchilla Scaling Law

The notes describe the relationship between **model parameters** and **training tokens**.

A useful way to think about it:

> Model size and training data should be balanced rather than simply making the model as large as possible.

### Older approach

```text
Huge model
   +
Not enough training data
   ↓
Wasted compute
```

### Better-balanced approach

```text
Smaller model
   +
More training data
   ↓
Better performance for the same compute
```

### Key takeaway

**More parameters alone do not guarantee better performance.**

Training data and model size need to be considered together.

---

# 5. What Are AI Benchmarks?

An **AI benchmark** is a standardized evaluation used to measure how well a model performs on a particular set of tasks.

Benchmarks can help us compare models, but they should not be treated as the complete definition of model quality.

---

# 6. Important Benchmarks

## GPQA

**GPQA — Graduate-Level Google-Proof Q&A**

### Evaluates

- PhD-level science expertise

### From the course notes

- Around **448 expert questions**

The benchmark is designed to test difficult scientific knowledge and reasoning.

---

## MMLU-Pro

### Evaluates

- Broad language and knowledge understanding

It is described as a more advanced and cleaned-up version of **MMLU**.

One distinction highlighted in the course:

- MMLU uses multiple-choice questions with fewer choices
- MMLU-Pro uses **10 choices**

---

## AIME

### Evaluates

- Mathematical reasoning

AIME contains difficult competitive mathematics problems associated with the prestigious **American Invitational Mathematics Examination**.

---

## LiveCodeBench

### Evaluates

- Coding ability

It evaluates code-focused LLMs using programming problems associated with platforms/contests such as:

- LeetCode
- AtCoder
- Codeforces

---

## MuSR

### Evaluates

- Logical reasoning

The benchmark focuses on logical deduction.

Example type:

> Analyze a complex mystery and determine who has the means, motive, and opportunity.

---

## HLE

**HLE — Humanity's Last Exam**

### Evaluates

- Very difficult academic knowledge
- Broad subject coverage
- Multimodal capabilities

The course describes it as containing thousands of challenging, subject-diverse, multimodal questions intended to represent extremely difficult academic evaluation.

---

# 7. Benchmark Comparison

| Benchmark | Main capability evaluated |
|---|---|
| **GPQA** | PhD-level science expertise |
| **MMLU-Pro** | Language and broad knowledge understanding |
| **AIME** | Mathematics |
| **LiveCodeBench** | Coding |
| **MuSR** | Logical reasoning |
| **HLE** | Extremely difficult, broad academic / multimodal intelligence |

### Important idea

Different benchmarks measure **different capabilities**.

Therefore:

```text
Highest benchmark score
        ≠
Best model for every application
```

---

# 8. Limitations of AI Benchmarks

Benchmarks are useful, but they have important limitations.

## 1. Training-data contamination

A model may have encountered benchmark questions or similar data during training.

This can make the benchmark score look better than the model's true generalization ability.

---

## 2. Benchmarks are not always consistently applied

Different evaluation setups can affect results.

Therefore, leaderboard numbers should be interpreted carefully.

---

## 3. Narrow scope

A benchmark normally measures a specific capability.

A model can perform extremely well in one area while being weaker in another.

Example:

```text
Excellent coding score
        ↓
Does NOT automatically mean
excellent reasoning / business performance
```

---

## 4. Difficult to measure nuanced reasoning

Some sophisticated reasoning abilities are difficult to capture with a fixed benchmark.

Real-world tasks can involve:

- Context
- Ambiguity
- Long workflows
- Domain-specific requirements
- Tool usage

A benchmark may not fully represent these situations.

---

## 5. Saturation

As models become very strong on a benchmark, the benchmark can become less useful for distinguishing between the strongest models.

```text
Benchmark becomes too easy
        ↓
Many models score highly
        ↓
Less useful for separating models
```

---

## 6. Overfitting

Models can become highly optimized for benchmark-style tasks without necessarily becoming equally capable across all real-world tasks.

This is another reason not to rely on a single leaderboard score.

---

# 9. A Practical LLM Evaluation Checklist

When choosing an LLM for a real project, consider multiple dimensions:

### Capability

- Does it perform well on the task?
- Is it good at coding?
- Reasoning?
- General knowledge?
- Multimodal tasks?

### Model characteristics

- Parameters
- Training tokens
- Context length
- Knowledge cutoff
- Chat / reasoning / hybrid
- Open-source / closed-source

### Production considerations

- Inference cost
- Training/fine-tuning cost
- Latency
- Speed
- Rate limits
- License
- Time to market

### Evaluation

- Relevant benchmarks
- Leaderboard position
- Real-world testing
- Task-specific evaluation

---

# 10. Key Takeaways

### Takeaway 1

**There is no single best LLM for every task.**

The right model depends on the requirements of the application.

### Takeaway 2

**Model size and training data should be considered together.**

This is one of the important ideas behind the Chinchilla Scaling Law.

### Takeaway 3

**Benchmarks are useful measurement tools, not absolute truth.**

Always understand what a benchmark actually evaluates.

### Takeaway 4

**Benchmark scores must be interpreted carefully.**

Data contamination, narrow scope, saturation, overfitting, and difficulty measuring nuanced reasoning can affect their usefulness.

### Takeaway 5

**Production decisions require more than benchmark scores.**

Cost, latency, speed, rate limits, licensing, and time to market can be just as important.

---

# Quick Revision

## Chinchilla Scaling Law

```text
Model parameters ↔ Training tokens
```

The key idea is to balance model size with sufficient training data rather than simply maximizing parameters.

## Benchmark Memory Trick

```text
GPQA          → Science
MMLU-Pro      → Knowledge / Language
AIME          → Math
LiveCodeBench → Coding
MuSR          → Reasoning
HLE           → Very difficult broad / multimodal knowledge
```

## Final Mental Model

```text
Choose an LLM
     ↓
Understand the task
     ↓
Compare model capabilities
     ↓
Check benchmarks
     ↓
Check limitations of benchmarks
     ↓
Check cost + latency + speed
     ↓
Check rate limits + license
     ↓
Test on the actual use case
     ↓
Select the right model
```

---

## One-Line Summary

> **LLM selection is not about finding the model with the highest score; it is about finding the model that provides the right capability, quality, cost, speed, and deployment fit for the actual task.**

---

## Day 16 Status

**Day 16/60 ✅**

### Topics Covered

- Choosing the right LLM
- LLM parameters
- Training tokens
- Context length
- Knowledge cutoff
- Open-source vs closed-source
- Chat vs reasoning vs hybrid models
- Inference cost
- Training cost
- Business cost
- Time to market
- Rate limits
- Speed
- Latency
- Licensing
- Chinchilla Scaling Law
- AI benchmarks
- GPQA
- MMLU-Pro
- AIME
- LiveCodeBench
- MuSR
- HLE
- Benchmark limitations
- Data contamination
- Narrow benchmark scope
- Saturation
- Overfitting
