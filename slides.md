---
# try also 'default' to start simple
theme: seriph
themeConfig:
  primary: '#ca9ee6'
layout: intro
title: Generating Code with OpenAPI
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
transition: slide-left
comark: true
duration: 35min
---

# Generating Code with OpenAPI

A dive into automatic code generation from OpenAPI specs

<div class="flex">
  <img src="/assets/orval.svg" class="max-w-50 mx-auto">
  <img src="/assets/hey-api-dark.svg" class="max-w-50 mx-auto">
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: center
hideInToc: true
---

# Table of contents

<Toc text-sm minDepth="1" maxDepth="2" />

---
layout: section
---

# How does this help us?

<p v-click>Generate API calls, typescript types, validators and wrappers; all from an OpenAPI specification</p>
<p v-click>Removes the need for writing boiler-plate code and creates a standardised output</p>

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
src: ./pages/using-generated-code-orval.md
---

---
src: ./pages/using-generated-code-hey-api.md
---

---
src: ./pages/taking-it-further.md
---

---
src: ./pages/hey-api-does-that.md
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
