---
theme: seriph
background: "/images/background.png"
title: Attention is more than what you need
titleTemplate: "%s"
info: |
    ## Slidev Starter Template
    Presentation slides for developers.

    Learn more at [Sli.dev](https://sli.dev)

author: Alireza Mohammadnezhad && Mahdi Khodabandeh 
class: text-center
highlighter: shiki
drawings:
    persist: false
transition: fade-out
mdc: true
hideInToc: true
---

<style>
  .token {
    margin: 4px;
    padding: 0 8px;
    border-radius: 20px;
    line-height: 88px;
  }
</style>

<h1>
  <span class="token" style="background-color: rgba(107, 64, 216, 0.7)">Attention</span><br/>
  <span class="token" style="background-color: rgba(104, 222, 122, 0.6)"> is</span>
  <span class="token" style="background-color: rgba(244, 172, 54, 0.6)"> more</span>
  <span class="token" style="background-color: rgba(239, 65, 70, 0.6)"> than</span>
  <span class="token" style="background-color: rgba(39, 181, 234, 0.6)"> you</span>
  <span class="token" style="background-color: rgba(107, 64, 216, 0.7)"> need</span>
</h1>
<!-- Alternate title: Transformers: The what, why & how -->


---
transition: fade-out
layout: two-cols
hideInToc: true
---

# Outline

- Transformers is a neural network architecture introduced in a 2017 paper by Vaswani et al. named: "Attention is all you need"
- Transformers outperform traditional RNNs and LSTM on many tasks.
- Widely used in natural language processing tasks, and extending it, is an active area of research
- It revolutionized NL but proofed beyond capable in vision and audio as well
- Transformers are based on "Self-Attention", allowing them to consider the entire context, instead of being limited immediate neighbors.

::right::

<div v-click >
<h3>Table of Contents:</h3>
<Toc minDepth="1" maxDepth="1" ></Toc> 
</div>

---
transition: fade-out
level: 2
---

# Pre-Transformer Summary

Early Beginnings of Theory
 - 1940s: Claude Shannon lays foundation for modern information theory, including concept of self-information
 - 1950s: Noam Chomsky's work on syntactic structures influences development of natural language processing (NLP)
Pre-Transformer Era
 - 1980s: Introduction of recurrent neural networks (RNNs) for sequence modeling
 - 1990s: Development of long short-term memory (LSTM) networks to address vanishing gradient problem
 - 2000s: Rise of convolutional neural networks (CNNs) for computer vision tasks
Graph Neural Networks (GNNs)
 - 2005: Gori et al. introduce Graph Neural Networks (GNNs) for graph-structured data
 - 2010s: GNNs gain popularity for tasks like node classification, graph classification, and graph generation
 - Why mentioned? Similarities to transformers in structure: both operate on structured data, use self-attention mechanisms, and can handle variable-length inputs

---
transition: fade-out
level: 2
---

# The Transformer Revolution
2017: Vaswani et al. introduce Transformer model in "Attention is All You Need" paper
Replaces RNNs and CNNs with self-attention mechanism for sequence-to-sequence tasks
Achieves state-of-the-art results in machine translation tasks

## Early Variants and Improvements
- 2018: BERT (Bidirectional Encoder Representations from Transformers) introduced by Google
Pre-trains language models on large datasets, achieving state-of-the-art results in many NLP tasks
- 2019: RoBERTa (Robustly Optimized BERT Pretraining Approach) introduced by Facebook AI
Further improves upon BERT with larger datasets and more efficient training
Scaling Up and Specialization
- 2019: GPT-2 (Generative Pre-trained Transformer 2) introduced by OpenAI
Large-scale language model with 1.5 billion parameters, demonstrating impressive text generation capabilities
- 2020: **GPT-3** introduced by OpenAI an Even larger model with 175 billion parameters, achieving state-of-the-art results in many NLP tasks, used in chatgpt early versions, which transformed world of AI forever 
- 2020: T5 (Text-to-Text Transformer) introduced by Google Unified framework for various NLP tasks, including text classification, sentiment analysis, and question answering

---
transition: fade-out
level: 2
---

# After GPT3, Gradual Move Toward Democratization

## 
 - 2020: Hugging Face's Transformers library makes pre-trained models widely available
 - 2020: EleutherAI's open-source models, including The Pile and GPT-Neo, challenges some early closed-source models
 - 2020: Stability AI was founded by Emad Mostaque, an entrepreneur and AI researcher

## New Methods
Newer Models and Advancements
2022: Ongoing research in:
Efficient transformer architectures (e.g., sparse attention, kernelization)
Multimodal transformers for combining text, image, and audio inputs
Explainability and interpretability of transformer models

---
transition: fade-out
layout: two-cols
---

# Transformers Architecture
At the core of this marvel is many smart mathematical ideas, of a system which 
 - Find connection between any pair of information units 
 - Is efficent to fine-tune
 - Is easy to back-propagate
 - Can run and train (in some aspects) highly in parallel.
 - Learns alot of complex patterns and adds the right non-linearity

::right::

<div v-click >
<h3>Table of Contents:</h3>
<Toc Toc minDepth="2" maxDepth="2"></Toc> 
</div>

---
transition: fade-out
level: 2
---

# A Glance at the Architecture

<!-- TODO: tokenize the part that says: "so we use tokens!" -->
- Text bodies and words are too big, Characters are too small, 
<span v-click class="rounded-lg m-0.5 pl-0.5 pr-0.5" style="background-color: rgba(107, 64, 216, 0.7)">so</span>
<span v-click class="rounded-lg m-0.5 pl-0.5 pr-0.5" style="background-color: rgba(244, 172, 54, 0.6)"> we</span>
<span v-click class="rounded-lg m-0.5 pl-0.5 pr-0.5" style="background-color: rgba(239, 65, 70, 0.6)"> use</span>
<span v-click class="rounded-lg m-0.5 pl-0.5 pr-0.5" style="background-color: rgba(39, 181, 234, 0.6)"> tokens</span>
<span v-click class="rounded-lg m-0.5 pl-0.5 pr-0.5" style="background-color: rgba(107, 64, 216, 0.7)">!</span>
<div v-click>

- Language modeling is all about predicting the next token
- Turns out just predicting the next token is general enough for lots of tasks
  - The model needs to know programming to predict a code token
  - It needs to have general knowledge of the world in case it needs to predict a capital name
  - Reasoning and logic is required to piece together what comes next
  - And so much more...

</div>

---
transition: fade-out
layout: two-cols
---

# LSTM
- LSTM is one form of RNN
- RNNs have a memory that is updated on each step
- We need to compute each step before doing the next
- This makes them sequential in nature
<!-- TODO: insert image of LSTM/RNN -->

---
level: 2
transition: fade-out
---

# RNN
- LSTM is one form of RNN
- RNNs have a memory that is updated on each step
- We need to compute each step before doing the next
- This makes them sequential in nature
<!-- TODO: insert image of LSTM/RNN -->

---
level: 2
layout: two-cols
---

# Transformer, Tho...
- Uses attention
- The idea of attention was initially proposed to boost LSTMs!
- What if we just used attention? Asked some researcher at Google
- The paper "Attention is all you need" proposed to use <u>only</u> attention

::right::
<center>
  <img src="/images/Attention.png" alt="A visualization of attention" width=250 height=200>
</center>

---
transition: fade-out
layout: two-cols
---

# A Revolution, and its future

It wont be the same again...
- What made transformers so big? (in parameter count)
- What made transformers so big? (in technology)

<!-- 
After transformers, People thought, world of NLP wont be the same ever again, after sometime, they figured out, world of AI wont be the same ever again, and now, the common belief is the world wont be the same ever again, hope for and footstep of AGI can be heard, from not so far. -->

---
transition: fade-out
level: 2
---

# What made transformers so big? (in parameter count)
- Promising Curve of Improvement
- They were more parallel!
- Attention is Parallel by Nature, and Our Computers (GPUs in particular) Love Parallel Computing
  - No memory (in LSTM sense), therefore no sequential computation
  - Each attention can be computed separately
- Parallelism ➡️ Easier Horizontal Scale

<!-- mostly simple linear formulas with highly parallel non-linearity -->

---
transition: fade-out
level: 2
---

# What made transformers so big? (in technology)

- Need for insight
- Unmatched Results!
- As Andrej Karpathy Says (Former OpenAI Employee and Chief of Tesla AI) ➡️
<!-- TODO: plot comparing parameter count of transformers with rnns -->

---
transition: fade-out
level: 2
---

<iframe class="slidev-full-iframe" src="https://www.youtube.com/embed/cdiD-9MMpb0?start=2035&amp;end=2071" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<div class="slidev-note">Courtesy of Lex Fridman Podcast</div>

<style>
.slidev-full-iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border: none;
}

.slidev-note {
  position: absolute;
  bottom: 0;
  right: 0;
  padding: 10px;
  background-color: rgba(0, 0, 0, 0.8);
  border-radius: 5px;
}
</style>

---

# Future
- The More Compute, The More Performant, But the Acceleration Seems Negative
- More Attention, More Researcher, More Attention!
- Quality Datasets
- Synthesis and Augmentation of Data
- Extending Context-Size
- Battle on Hardware

---

# Leading LLMs
- Small models (for Mobile and IoT)
  - Phi series (Microsoft)
  - Gemma (Google)
  - Llama (Meta)
- Grand Models
  - Claude 3 Opus (Anthropic)
  - GPT-4 (OpenAI)
  - Gemeni-2 (Google)

# Toward MultiModality
- What it means?
- Why it matters?


---
layout: center
class: text-center
---

<h1>
  <span class="token" style="background-color: rgba(244, 172, 54, 0.6)">&lt;eos/&gt;</span>
</h1>

<style>
  h1 {
    font-size: 100px;
  }

  .token {
    margin: 4px;
    padding: 0 8px;
    border-radius: 20px;
  }
</style>
