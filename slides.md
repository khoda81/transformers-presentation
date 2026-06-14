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

by  Mahdi Khodabandeh &  Reyhane parsa

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


<div class="timeline">
    <div class="timeline-step" style="--delay: 0ms">
        <span class="timeline-date">Before 1990</span>
        <span class="timeline-label">Statistical language models</span>
    </div>
    <div class="timeline-step" style="--delay: 140ms">
        <span class="timeline-date">1990s</span>
        <span class="timeline-label">RNNs</span>
    </div>
    <div class="timeline-step" style="--delay: 280ms">
        <span class="timeline-date">1997</span>
        <span class="timeline-label">LSTMs</span>
    </div>
    <div class="timeline-step" style="--delay: 420ms">
        <span class="timeline-date">2014</span>
        <span class="timeline-label">Attention for LSTMs</span>
    </div>
    <div class="timeline-step" style="--delay: 560ms">
        <span class="timeline-date">2017</span>
        <span class="timeline-label">Transformers</span>
    </div>
    <div class="timeline-step" style="--delay: 700ms">
        <span class="timeline-date">Today</span>
        <span class="timeline-label">LLMs</span>
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

<!-- The encoder must compress the entire sequence into a fixed-size representation. Long-range dependencies are difficult to learn due to vanishing gradients. -->

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


<!-- Attention was first introduced as an extension to encoder-decoder RNN/LSTM models for machine translation. -->

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
hideInToc: true
---

# Key Innovations of "Attention Is All You Need"

<div class="text-center opacity-80 mb-6">
  What made this paper a breakthrough?
</div>

<div class="grid grid-cols-2 gap-4 max-w-4xl mx-auto">

<div class="p-4 rounded-lg border border-gray-200 dark:border-gray-700 shadow-sm hover:shadow-md transition">

<div class="flex items-center gap-3 mb-2">
  <div class="w-7 h-7 rounded-full bg-purple-500 text-white flex items-center justify-center text-sm font-bold">1</div>
  <span class="font-semibold text-lg">Pure self-attention</span>
</div>
<div class="text-sm text-gray-600 dark:text-gray-400 ml-10">
  No recurrence or convolution at all
</div>

</div>

<div class="p-4 rounded-lg border border-gray-200 dark:border-gray-700 shadow-sm hover:shadow-md transition">

<div class="flex items-center gap-3 mb-2">
  <div class="w-7 h-7 rounded-full bg-purple-500 text-white flex items-center justify-center text-sm font-bold">2</div>
  <span class="font-semibold text-lg">Multi-head attention</span>
</div>
<div class="text-sm text-gray-600 dark:text-gray-400 ml-10">
  Attending to different representation subspaces
</div>

</div>

<div class="p-4 rounded-lg border border-gray-200 dark:border-gray-700 shadow-sm hover:shadow-md transition">

<div class="flex items-center gap-3 mb-2">
  <div class="w-7 h-7 rounded-full bg-purple-500 text-white flex items-center justify-center text-sm font-bold">3</div>
  <span class="font-semibold text-lg">Positional encoding</span>
</div>
<div class="text-sm text-gray-600 dark:text-gray-400 ml-10">
  Injecting sequence order information
</div>

</div>

<div class="p-4 rounded-lg border border-gray-200 dark:border-gray-700 shadow-sm hover:shadow-md transition">

<div class="flex items-center gap-3 mb-2">
  <div class="w-7 h-7 rounded-full bg-purple-500 text-white flex items-center justify-center text-sm font-bold">4</div>
  <span class="font-semibold text-lg">Scaled dot‑product attention</span>
</div>
<div class="text-sm text-gray-600 dark:text-gray-400 ml-10">
  Efficient and fast to compute
</div>

</div>

<div class="p-4 rounded-lg border border-gray-200 dark:border-gray-700 shadow-sm hover:shadow-md transition">

<div class="flex items-center gap-3 mb-2">
  <div class="w-7 h-7 rounded-full bg-purple-500 text-white flex items-center justify-center text-sm font-bold">5</div>
  <span class="font-semibold text-lg">Encoder‑decoder with only attention</span>
</div>
<div class="text-sm text-gray-600 dark:text-gray-400 ml-10">
  Fully parallelizable architecture
</div>

</div>

<div class="p-4 rounded-lg border border-gray-200 dark:border-gray-700 shadow-sm hover:shadow-md transition">

<div class="flex items-center gap-3 mb-2">
  <div class="w-7 h-7 rounded-full bg-purple-500 text-white flex items-center justify-center text-sm font-bold">6</div>
  <span class="font-semibold text-lg">Enabling massive scaling</span>
</div>
<div class="text-sm text-gray-600 dark:text-gray-400 ml-10">
  Training on thousands of GPUs became possible
</div>

</div>

</div>

<style>
/* Optional: Adjust for dark/light mode automatically handled by Slidev */
</style>

---
layout: fact
class: text-center
hideInToc: true
---

# Conclusion

<br />

<div class="grid grid-cols-1 gap-4 text-left max-w-2xl mx-auto">

<div class="flex items-start gap-3">
  <div class="text-3xl"></div>
  <div>
    <strong>Removed the sequential bottleneck</strong><br />
    <span class="text-sm opacity-80">Transformers unlocked <span class="font-mono">parallel training</span> at scale</span>
  </div>
</div>

<div class="flex items-start gap-3">
  <div class="text-3xl"></div>
  <div>
    <strong>Set the stage for LLMs</strong><br />
    <span class="text-sm opacity-80">GPT · BERT · Llama · and every modern model</span>
  </div>
</div>

<div class="flex items-start gap-3">
  <div class="text-3xl"></div>
  <div>
    <strong>Inspired a new research direction</strong><br />
    <span class="text-sm opacity-80">“<Tokenize :tokens="['Attention', ' is', ' more', ' than', ' you', ' need']" />”</span>
  </div>
</div>

</div>

<br />

<hr class="w-24 mx-auto my-4 border-t-2 border-gray-400 opacity-50" />

<div class="text-lg font-medium">
  <span class="line-through opacity-60">LSTMs are dead</span>   →  
  <span class="text-gradient bg-gradient-to-r from-purple-400 to-green-400 bg-clip-text text-transparent">Transformers became the new king</span>
</div>

<style>
.text-gradient {
  background-clip: text;
  -webkit-background-clip: text;
}
</style>

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
