---
# try also 'default' to start simple
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides, markdown enabled
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply any unocss classes to the current slide
class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true
---

# Frida Stack v1



<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
---

# Web dev en 2024

El ecosistema web cambia mucho y muy rápido. Siempre salen nuevos frameworks y nuevas formas de resolver problemas. Aqui un breve overview de los últimos trends:

- 📝 **SSR** - Server side rendering. Paradigma popularizado por Vercel y Next.js
- 📝 **No client-side JS** - Minimizar la cantidad de javascript en el cliente. *optimización*
- 🎨 **DX** - La Developer Experience ahora es considerada muy importante en el desarrollo de aplicaciones.
- 🧑‍💻 **TS** - TypeScript elimina las debilidades de JavaScript y mejora DX.
- 🤹 **Frontend Libraries/Frameworks** - <span v-mark.circle.orange="2">React</span>, Vue, Angular, Svelte, Quik, Preact, HTMX, etc.
- 📤 **CSS?** - Tailwind CSS, UnoCSS, StyleX, (❌ styled components)
- <span v-mark.red="1">🎥 **Data fetching** - Client side vs Server side</span>
- 🛠 **Manage State** - Realmente necesario?
- 🛠 **SOON: React Compiler** - Adios useCallback y useMemo
- 


<br>
<br>

¡Más detalles muy pronto!

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
Here is another comment.
-->

---
src: ./pages/about-useEffect.md
transition: slide-up
---


---
src: ./pages/data-fetching-in-react.md
transiton: slide-up
---

---
src: ./pages/nuestro-panorama.md
transition: fade-out
---

---
src: ./pages/tanstack-query.md
transition: slide-right
---

---
layout: image
image: /images/tanstack-query-example.jpeg
---

---
---

# ¿Cómo lo usa Innovation con Firebase?



[Documentations](https://sli.dev) · [GitHub](https://github.com/slidevjs/slidev) · [Showcases](https://sli.dev/showcases.html)
