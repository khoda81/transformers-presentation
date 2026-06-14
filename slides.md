---
theme: ./theme
background: "./images/background.png"
# some information about your slides, markdown enabled
title: Attention is more than what you need
titleTemplate: "%s"
info: false
author: Mahdi Khodabandeh
selectable: false
# force color schema for the slides, can be 'auto', 'light', or 'dark'
colorSchema: light
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
hideInToc: true

duration: 7min
timer: stopwatch
---

<h1>
    <!--  :colors='["rgba(107, 64, 216, 0.5)", "rgba(104, 222, 122, 0.6)", "rgba(244, 172, 54, 0.6)", "rgba(239, 65, 70, 0.6)", "rgba(39, 181, 234, 0.6)", "rgba(107, 64, 216, 0.7)"]' -->

  <Tokenize :tokens="['Attention']" />
  <br/>
  <Tokenize :initialColorIndex="1" :tokens="[' is', ' more', ' than', ' you', ' need']" />
</h1>

by Mahdi Khodabandeh

<img id="logo" :src="'./images/tehran_universiy_logo.png'" alt="Logo of Tehran University" />

---
layout: two-cols
hideInToc: true
---

# Outline
<!-- TODO: -->

::right::

<Toc />

---
layout: full
hideInToc: true
---

# Language modeling

<div>
    <p class="lead">Language modeling is predicting the next token.</p>
    <p>Working with text is hard, so we use tokens.</p>
</div>
<div id="language-model-example">
    <div class="prompt-tokens">
        <Tokenize animate :tokens="['The', ' quick', ' brown', ' fox', ' jumps']" />
    </div>
    <div class="distribution">
        <div class="prediction" style="--probability: 0.91; --delay: 650ms"><Tokenize :colors="['#f8fafc33']" :tokens="[' over']" /></div>
        <div class="prediction" style="--probability: 0.51; --delay: 750ms"><Tokenize :colors="['#f8fafc33']" :tokens="[' up']" /></div>
        <div class="prediction" style="--probability: 0.28; --delay: 850ms"><Tokenize :colors="['#f8fafc33']" :tokens="[' out']" /></div>
        <div class="prediction" style="--probability: 0.08; --delay: 950ms"><Tokenize :colors="['#f8fafc33']" :tokens="[' on']" /></div>
        <div class="prediction" style="--probability: 0.07; --delay: 1050ms"><Tokenize :colors="['#f8fafc33']" :tokens="[' in']" /></div>
    </div>
</div>

<!--
Think about it as auto-complete for natural language.
The token distribution.
-->

<SlideCurrentNo />

---
hideInToc: true
---

# LSTMs (RNNs)

<v-clicks>

- LSTM is one form of RNN
- RNNs have a memory that is updated on each step
- We need to compute each step before doing the next

</v-clicks>

<br />

<v-click>
    <img class="slide-img diagram-reveal" :src="'./images/LSTM.png'" alt="A diagram of LSTM" />
</v-click>

<!-- 
How to read the diagram.
 -->
<SlideCurrentNo />

---

# RNNs were unstoppable!

<br />

<div class="timeline">
    <div class="timeline-step" style="--delay: 0ms">
        <span class="timeline-date">1950s</span>
        <span class="timeline-label">Early statistical models like n-grams</span>
    </div>
    <div class="timeline-step" style="--delay: 140ms">
        <span class="timeline-date">1980s</span>
        <span class="timeline-label">RNNs</span>
    </div>
    <div class="timeline-step" style="--delay: 280ms">
        <span class="timeline-date">1990s-2000s</span>
        <span class="timeline-label">LSTMs</span>
    </div>
    <div class="timeline-step" style="--delay: 420ms">
        <span class="timeline-date">2010s</span>
        <span class="timeline-label">Attention introduced</span>
    </div>
    <div class="timeline-step" style="--delay: 560ms">
        <span class="timeline-date">2017-present</span>
        <span class="timeline-label">Transformers</span>
    </div>
</div>

<!-- TODO: make this into a timeline -->

---
layout: fact
---

# What happened?
## RNNs had some problems...

---
---

# The memory bottleneck

<br />
<br />

<v-click>
    <img class="slide-img diagram-reveal" :src="'./images/LSTM.png'" alt="A diagram of LSTM" />
</v-click>


<SlideCurrentNo />
<!-- TODO: add a bunch of arrows as we click -->

<!-- The memory size is fixed no matter how long the sequence is. This is called the vanishing gradient problem. -->

---
hideInToc: true
---

# The fix

<v-clicks>

- What if we had an skip route?
- This is where attention was born
- If you want something, just ask!

</v-clicks>

<br />

<v-click>
    <img class="slide-img diagram-reveal" :src="'./images/LSTM-with-attention.png'" alt="A diagram of LSTM with attention" />
</v-click>


<!-- The idea of attention was initially proposed to boost LSTMs! -->

---
---

# Attention

<v-click>

- It has three parts:

</v-click>

<v-click>

- Key
- Query
- Value

</v-click>

<v-click>
    <img class="slide-img diagram-reveal" :src="'./images/Attention.png'" alt="A diagram of attention" />
</v-click>

<SlideCurrentNo />

---
---

# What about performance?

<v-click>

1. Computers (specially GPUs) hate sequential workflows
- RNNs are **sequential** in nature

</v-click>

<v-click>

2. Computers (specially GPUs) love parallelism
- Attention is **parallel** in nature

</v-click>

<v-switch>
  <template #0> <img :src="'./images/LSTM-with-attention.png'" alt="A diagram of LSTM with attention" /> </template>
  <template #1> <img :src="'./images/RNN-is-sequential.png'" alt="Showing rnn being sequential" /> </template>
  <template #2> <img :src="'./images/Attention-is-parallel.png'" alt="Showing attention being parallel" /> </template>
</v-switch>

<!-- GPUs have thousands of cores! Attention + GPU go brr -->

---
---

# What if attention was all you needed?
Asked some researcher at Google

<br />

<v-click>

The paper "Attention is all you need" proposed to use <u>only</u> attention.

</v-click>

<v-click>
    <img class="slide-img diagram-reveal" :src="'./images/Attention-is-all-you-need.png'" alt="Showing attention being parallel" />
</v-click>

<!-- 
Tip #1 in optimization! Do less work!
Turns out, it is more than you need :)
 -->

---
---

# A transformer block
<center>
    <v-click>
        <img class="slide-img diagram-reveal" :src="'./images/Transformer-block-attention-only.png'" alt="A Transformer block" />
    </v-click>
</center>
<!-- TODO:
 -->

<SlideCurrentNo />

---
---

# The full architecture

<v-click>

Originally had two parts

</v-click>

<v-click>
    <img class="slide-img diagram-reveal" :src="'./images/EncoderDecoder.png'" alt="Architecture" />
</v-click>
<!-- 

 -->

---
layout: fact
---

# What made transformers so big?

They were parallel!
<!-- TODO: plot comparing parameter count of transformers with rnns -->

---

# Size matters (in deep learning)

<div class="size-triangle">
    <div class="pillar pillar-compute" style="--delay: 0ms">
        <strong>Compute</strong>
        <span>More training steps</span>
    </div>
    <div class="pillar pillar-data" style="--delay: 160ms">
        <strong>Data</strong>
        <span>More examples</span>
    </div>
    <div class="pillar pillar-model" style="--delay: 320ms">
        <strong>Model</strong>
        <span>Better predictions</span>
    </div>
    <div class="triangle-core" style="--delay: 520ms">Scale</div>
</div>

<!-- 
This does not seem to stop (aka. our models seem to always get better as we make them bigger)
This is also where the term LLM (Large Language Model) comes from
 -->

---
layout: fact
---

# Conclusion
LSTMs are dead! Long live transformers!

<!-- 
This does not seem to stop (aka. our models seem to always get better as we make them bigger)
This is also where the term LLM (Large Language Model) comes from
 -->

---
layout: end
---

<h1 :style="{ fontSize: 5 + 'rem' }">
  <Tokenize :tokens="['<end/>']" />
</h1>

<!-- TODO: this page is too empty -->
