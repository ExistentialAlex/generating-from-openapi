---
# try also 'default' to start simple
theme: seriph
themeConfig:
  primary: '#ca9ee6'
layout: intro
title: Orval
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
transition: slide-left
comark: true
duration: 35min
---

# Orval

A dive into automatic code generation from OpenAPI specs

<img src="/assets/emblem.svg" class="max-w-50 mx-auto">

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: center
---

# Table of contents

<Toc text-sm minDepth="1" maxDepth="2" />

---
layout: section
---

# What is Orval?

<v-click>"Transform your OpenAPI specs into type-safe clients, mocks, and validators."</v-click>

<!--
Here is another comment.
-->

---
src: ./pages/in-practice.md
---

---
src: ./pages/what-we-end-up-with.md
---

---
src: ./pages/using-generated-code.md
---

---
src: ./pages/taking-it-further.md
---

---
src: ./pages/wrap-up.md
---


---
layout: center
class: text-center
---

# Questions

[Documentation](https://orval.dev/) · [GitHub](https://github.com/orval-labs/orval)
