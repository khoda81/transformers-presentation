---
# try also 'default' to start simple
theme: default
background: "/images/background.png"
# some information about your slides, markdown enabled
title: Attention is more than what you need
titleTemplate: "%s"
info: |
    ## Slidev Starter Template
    Presentation slides for developers.

    Learn more at [Sli.dev](https://sli.dev)

author: Mahdi Khodabandeh
class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
    persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: fade-out
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true

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
---

# A bit of history

Language modeling has been around forever!
<br/>
<br/>

<!-- TODO: make this into a timeline -->
- Pre-machine-learning (1966-1997)
- LSTMs (1997-2017)
- Transformer based Large Language Models (2017-now)

<!-- TODO: tokenize the headings -->

---
transition: fade-out
---

# A bit of background

<!-- TODO: tokenize the part that says: "so we use tokens!" -->
- Working with text is hard, so we use tokens!
- Language modeling is the art of predicting the next token
- Turns out just predicting the next token is so general
  - The model needs to know programming to predict a code token
  - It needs to have general knowledge of the world in case it needs to predict a capital name
  - Reasoning and logic is required to piece together what comes next
  - And so much more...

---

# LSTM you say?
- LSTM is one form of RNN
- RNNs have a memory that is updated on each step
- We need to compute each step before doing the next
- This makes them sequential in nature
<!-- TODO: insert image of LSTM/RNN -->

---

# Transformer you say?
- They use attention
<!-- TODO: insert attention image -->
- The idea of attention was initially proposed to boost LSTMs!
- What if we just used attention? Asked some researcher at Google
- The paper "Attention is all you need" proposed to use <u>only</u> attention

---

# What made transformers so big? (in technology)
- They were more parallel!
- Our computers (GPUs in particular) love parallel computing
- Since they are parallel they get big

---

# Attention + GPU go brr
- No memory, therefore no sequential computation
- Each attention can be computed separately
<!-- TODO: insert attention image -->

---

# What made transformers so big? (in parameter count)
- And transformers get BIG (like REALLY BIG)
<!-- TODO: plot comparing parameter count of transformers with rnns -->

---

# Size matters (in deep learning)
The more compute you have => The more data you can process => The better your model gets
This does not seem to stop (aka. our models seem to always get better as we make them bigger)
This is also where the term LLM (Large Language Model) comes from

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
