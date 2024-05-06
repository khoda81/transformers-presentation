---
theme: default
background: "/images/background.png"
# some information about your slides, markdown enabled
title: Attention is more than what you need
titleTemplate: "%s"
info: false
author: Mahdi Khodabandeh
# controls whether texts in slides are selectable
selectable: true
# force color schema for the slides, can be 'auto', 'light', or 'dark'
colorSchema: dark
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
    persist: false

# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: fade-out
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true

layout: cover
---

<h1>
  <Tokenize :tokens="['Attention']" />
  <br/>
  <Tokenize :initialColorIndex="1" :tokens="[' is', ' more', ' than', ' you', ' need']" />
</h1>


by Mahdi Khodabandeh

<img id="logo" src="/images/guilan_universiy_logo.png" alt="Logo of Guilan University" />

<!-- 
What is language modeling?
Why is it important? Just predicting tokens forces you to know a lot of things. therefore it became the pinnacle task of AI development
Lets take a sentence (select a classic example!), tokenize it, and start predicting!
LSTMs (RNNs), the initial idea.
They were unstoppable!
What happened? Transformers!
The vanishing gradient problem (memory bottleneck)
The solution (Attention)
Another problem (Calculating all these connections is way too slow)
Tip #1 in optimization! Do less work! (Remove the sequential connections)
Attention is all you need! (The paper)
We can also do parallelism (It runs fast on GPU)
And, this was why transformers are everywhere! (Conclusion)
 -->

---
layout: two-cols
---

# Outline
<!-- TODO: -->

::right::

<Toc />

---
---

# What is language modeling?

Language modeling is the art of predicting the next token

<br />

- Working with text is hard, so we use tokens!
- For Example:

<br />
<br />

<div id="tokenization-example">
    <Tokenize :tokens="['The', ' quick', ' brown', ' fox', ' jumps', ' over', ' the', ' lazy', ' dog', '.']" />
    <!-- TODO: Add a vertical distribution visualizer. -->
</div>

---
---

# What is a language model?

<!-- Its the thing that predicts the next token. -->

---

# Anything is language modeling...
And language modeling is everything!

<!-- TODO: break down this slide -->
<!-- TODO: add examples of tasks that are language modeling -->
<!-- TODO: add examples of knowledge that language modeling requires -->

- Turns out just predicting the next token is so general
  - The model needs to know programming to predict a code token
  - You need to know different languages
  - It needs to have general knowledge of the world in case it needs to predict a capital name
  - Reasoning and logic is required to piece together what comes next
  - And so much more...

---

# LSTMs (RNNs)

- LSTM is one form of RNN
- RNNs have a memory that is updated on each step
- We need to compute each step before doing the next

<!-- TODO: insert a diagram of LSTM/RNN -->

---

# RNNs were unstoppable!
<!-- TODO: why? -->

---

# What happened?
Transformers!

- RNNs had some problems...
<!-- TODO: insert a diagram of LSTM/RNN -->

---

# The memory bottleneck

<!-- TODO: insert a diagram -->
<!-- The memory size is fixed no matter how long the sequence is. This is called the vanishing gradient problem. -->

---

# The fix

- What if we had an skip route?
- This is where attention was born
- If you want something, just ask!
<!-- TODO: insert diagram of attention -->

<!-- The idea of attention was initially proposed to boost LSTMs! -->

---
hideInToc: true
----

# The fix

- It has three parts:
    1. Key
    2. Query
    3. Value

<!-- TODO: insert diagram of attention -->

---

# What about performance?

1. Computers (specially GPUs) hate sequential workflows
    - RNNs are **sequential** in nature
2. Computers (specially GPUs) love parallelism
    - Attention is **parallel** in nature

<!-- TODO: insert computation graph -->

<!-- GPUs have thousands of cores! Attention + GPU go brr -->

---

# What if attention was all you needed?

- What if we just used attention? Asked some researcher at Google
- The paper "Attention is all you need" proposed to use <u>only</u> attention
<!-- Turns out, it is more than you need :) -->

---

# What made transformers so big?

They were parallel!
<!-- TODO: plot comparing parameter count of transformers with rnns -->

---

# Size matters (in deep learning)

- Deep learning cycle
    1. The more compute you have 
    2. The more data you can process 
    3. The better your model gets

<!-- 
This does not seem to stop (aka. our models seem to always get better as we make them bigger)
This is also where the term LLM (Large Language Model) comes from
 -->

---
layout: center
class: text-center
---

<h1 :style="{ fontSize: 5 + 'rem' }">
  <Tokenize :tokens="['<eos/>']" />
</h1>

<!-- TODO: this page is too empty -->
