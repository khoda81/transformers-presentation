---
theme: ./theme
background: "/images/background.png"
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
---

<h1>
    <!--  :colors='["rgba(107, 64, 216, 0.5)", "rgba(104, 222, 122, 0.6)", "rgba(244, 172, 54, 0.6)", "rgba(239, 65, 70, 0.6)", "rgba(39, 181, 234, 0.6)", "rgba(107, 64, 216, 0.7)"]' -->

  <Tokenize :tokens="['Attention']" />
  <br/>
  <Tokenize :initialColorIndex="1" :tokens="[' is', ' more', ' than', ' you', ' need']" />
</h1>

by  Mahdi Khodabandeh &  Reyhane parsa

<img id="logo" src="/images/tehran_universiy_logo.png" alt="Logo of Guilan University" />

---
layout: two-cols
hideInToc: true
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

<v-click>

- Working with text is hard, so we use tokens!
</v-click>

<v-click>

- For Example:

<br />
<br />

<div id="tokenization-example">
    <Tokenize :tokens="['The', ' quick', ' brown', ' fox', ' jumps', ' over', ' the', ' lazy', ' dog', '.']" />
</div>
</v-click>

<style>
    #tokenization-example {
        font-size: 2rem;
    }
</style>

<!-- 
Think about it as auto-complete for natural language
 -->

---
layout: full
hideInToc: true
---

# What is a language model?

<br />

<div id="language-model-example">
    <div>
        <Tokenize :tokens="['The', ' quick', ' brown', ' fox', ' jumps']" />
    </div>
    <div class="distribution">
        <div :style="{ opacity: '90.8119%' }"><Tokenize :colors="['#444a']" :tokens="[' over']" /></div>
        <div :style="{ opacity: '50.6378%' }"><Tokenize :colors="['#444a']" :tokens="[' up']" /></div>
        <div :style="{ opacity: '27.5646%' }"><Tokenize :colors="['#444a']" :tokens="[' out']" /></div>
        <div :style="{ opacity: '8.3804%' }"><Tokenize :colors="['#444a']" :tokens="[' on']" /></div>
        <div :style="{ opacity: '7.4399%' }"><Tokenize :colors="['#444a']" :tokens="[' in']" /></div>
        <div :style="{ opacity: '7.1968%' }"><Tokenize :colors="['#444a']" :tokens="[' off']" /></div>
        <div :style="{ opacity: '6.5143%' }"><Tokenize :colors="['#444a']" :tokens="[' into']" /></div>
        <div :style="{ opacity: '5.3833%' }"><Tokenize :colors="['#444a']" :tokens="[' from']" /></div>
        <div :style="{ opacity: '4.7140%' }"><Tokenize :colors="['#444a']" :tokens="[' to']" /></div>
        <div :style="{ opacity: '1.4568%' }"><Tokenize :colors="['#444a']" :tokens="[' and']" /></div>
    </div>
</div>

<style>
    #language-model-example {
        font-size: 3rem;
        padding: auto;
        display: flex;
    }

    .distribution {
        display: flex;
        flex-direction: column;
        align-items: flex-start; /* Align items to the start of the column */
    }

    .distribution div {
        margin-bottom: 5px; /* Add margin between items */
    }
</style>

<!--
Its the thing that predicts <u>only</u> the next token.
The token distribution.
-->

---
hideInToc: true
---

# Everything is language modeling...
And language modeling is everything!

- Turns out just predicting the next token is so general
  - The model needs to know programming to predict a code token
  - You need to know different languages
  - Needs to answer questions
  - It needs to have general knowledge of the world in case it needs to predict a capital name
  - Reasoning and logic is required to piece together what comes next
  - And so much more...

<!-- TODO: add examples for how to abuse -->

---
hideInToc: true
---

# LSTMs (RNNs)

- LSTM is one form of RNN
- RNNs have a memory that is updated on each step
- We need to compute each step before doing the next

<br />

<img src="/images/LSTM.png" alt="A diagram of LSTM" />

<!-- 
How to read the diagram.
 -->

---

# RNNs were unstoppable!

<br />

1. 1950s: Early statistical models like n-grams
2. 1980s: RNNs
3. 1990s-2000s: LSTMs
4. 2010s: Attention introduced
5. 2017-present: Transformers

<!-- TODO: make this into a timeline -->

---
layout: fact
---

# What happened?
## RNNs had some problems...

---

# The memory bottleneck

<br />
<br />

<img src="/images/LSTM.png" alt="A diagram of LSTM" />
<!-- TODO: add a bunch of arrows as we click -->

<!-- The memory size is fixed no matter how long the sequence is. This is called the vanishing gradient problem. -->

---
hideInToc: true
---

# The fix

- What if we had an skip route?
- This is where attention was born
- If you want something, just ask!

<br />

<v-click>
    <img src="/images/LSTM-with-attention.png" alt="A diagram of LSTM with attention" />
</v-click>

<!-- The idea of attention was initially proposed to boost LSTMs! -->

---

# Attention

- It has three parts:
    1. Key
    2. Query
    3. Value

<img src="/images/Attention.png" alt="A diagram of attention" />

---

# What about performance?

1. Computers (specially GPUs) hate sequential workflows
    - RNNs are **sequential** in nature
2. Computers (specially GPUs) love parallelism
    - Attention is **parallel** in nature

<v-switch>
  <template #0> <img src="/images/LSTM-with-attention.png" alt="A diagram of LSTM with attention" /> </template>
  <template #1> <img src="/images/RNN-is-sequential.png" alt="Showing rnn being sequential" /> </template>
  <template #2> <img src="/images/Attention-is-parallel.png" alt="Showing attention being parallel" /> </template>
</v-switch>

<!-- GPUs have thousands of cores! Attention + GPU go brr -->

---

# What if attention was all you needed?
Asked some researcher at Google

<br />

The paper "Attention is all you need" proposed to use <u>only</u> attention.

<img src="/images/Attention-is-all-you-need.png" alt="Showing attention being parallel" />

<!-- 
Tip #1 in optimization! Do less work!
Turns out, it is more than you need :)
 -->

---

# A transformer block
<center>
    <img src="/images/Transformer-block-attention-only.png" alt="A Transformer block" />
</center>
<!-- TODO:
 -->

---

# The full architecture

Originally had two parts

<img src="/images/EncoderDecoder.png" alt="Architecture" />
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

- Deep learning cycle
    1. The more compute you have 
    2. The more data you can process 
    3. The better your model gets

<!-- 
This does not seem to stop (aka. our models seem to always get better as we make them bigger)
This is also where the term LLM (Large Language Model) comes from
 -->
---
hideInToc: true
katex: true
---

# Key Innovations of "Attention Is All You Need"

<div class="text-center text-gray-500 mb-6 text-sm">
  What made this paper a breakthrough?
</div>

<div class="grid grid-cols-2 gap-4">

<!-- Column 1 -->
<div class="space-y-4">

<div class="bg-white dark:bg-gray-800 rounded-xl p-4 shadow-sm border-l-4 border-purple-500">
  <div class="font-bold text-purple-700 dark:text-purple-300">1. Pure self-attention</div>
  <div class="text-sm text-gray-600 dark:text-gray-300">No recurrence or convolution — fully parallelizable within a sequence.</div>
</div>

<div class="bg-white dark:bg-gray-800 rounded-xl p-4 shadow-sm border-l-4 border-purple-500">
  <div class="font-bold text-purple-700 dark:text-purple-300">2. Multi-head attention</div>
  <div class="text-sm text-gray-600 dark:text-gray-300">Multiple heads in parallel → different representation subspaces.</div>
</div>

<div class="bg-white dark:bg-gray-800 rounded-xl p-4 shadow-sm border-l-4 border-purple-500">
  <div class="font-bold text-purple-700 dark:text-purple-300">3. Sinusoidal positional encoding</div>
  <div class="text-sm text-gray-600 dark:text-gray-300 mb-1">Injecting sequence order:</div>
  <div class="text-xs text-gray-500 mt-1">Different frequencies for each dimension.</div>
</div>

</div>

<!-- Column 2 -->
<div class="space-y-4">

<div class="bg-white dark:bg-gray-800 rounded-xl p-4 shadow-sm border-l-4 border-purple-500">
  <div class="font-bold text-purple-700 dark:text-purple-300">4. Scaled dot‑product attention</div>
  <div class="text-sm text-gray-600 dark:text-gray-300 mb-1">Efficient matrix‑based attention:</div>
</div>

<div class="bg-white dark:bg-gray-800 rounded-xl p-4 shadow-sm border-l-4 border-purple-500">
  <div class="font-bold text-purple-700 dark:text-purple-300">5. Encoder‑decoder with only attention</div>
  <div class="text-sm text-gray-600 dark:text-gray-300">No RNN/CNN → fully parallel training and long-range dependencies.</div>
</div>

<div class="bg-white dark:bg-gray-800 rounded-xl p-4 shadow-sm border-l-4 border-purple-500">
  <div class="font-bold text-purple-700 dark:text-purple-300">6. Enabling massive scaling</div>
  <div class="text-sm text-gray-600 dark:text-gray-300">Parallel processing across all positions → training on thousands of GPUs.<br/>
  <span class="text-xs text-gray-500">(Matrix multiplication replaces sequential loops)</span>
  </div>
</div>

</div>

</div>

<div class="text-center text-xs text-gray-400 mt-6">
  — These six innovations made Transformers the dominant architecture since 2017 —
</div>
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
