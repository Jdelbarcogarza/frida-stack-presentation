---
# try also 'default' to start simple
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
author: "Jorge Del Barco Garza"
# background: https://cover.sli.dev
# some information about your slides, markdown enabled
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply any unocss classes to the current slide
class: text-center bg-gradient-to-b from-zinc-900 from-90% to-purple-700
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



<div class="pt-4 flex flex-col items-center">
<p class="absolute top-8 right-8 text-sm rotate-20">(Made with Tailwind CSS ✨)</p>
<img src="/images/fridagpt_1.png" class="size-64" />
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline mt-8"/>
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

- 📝 **SSR** - Server side rendering. Correr código del lado del servidor
- 📝 **No client-side JS** - Minimizar la cantidad de javascript en el cliente. *optimización*
- 🎨 **DX** - La Developer Experience ahora es considerada muy importante en el desarrollo de aplicaciones.
- 🧑‍💻 **TS** - TypeScript elimina las debilidades de JavaScript y mejora DX.
- 🤹 **Frontend Libraries/Frameworks** - <span v-mark.circle.orange="2">React</span>, Vue, Angular, Svelte, Quik, Preact, HTMX, Alpine.js etc.
- 📤 **CSS** - Tailwind CSS (casi un estándar), UnoCSS, StyleX, (❌ styled components)
- <span v-mark.red="1">🎥 **Data fetching** </span>- Client side vs Server side
- 🛠 **Manage State** - Zustand, Jotai, Valtio, MobX, Redux
- 🛠 **SOON: React Compiler** - Adios useCallback y useMemo


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
layout: cover
---

---
layout: image
image: /images/tanstack-query-example.jpeg
---

---

# ¿Tastack Query 🤝 Firebase?
Primero escribamos nuestra llamada a la DB en una Async function.

````md magic-move

```ts
// Gets chats corresponding to current dataset
  const getUserChats = async (): Promise<Chat[]> => {
    try {
      const collectionRef = collection( fs, "datasets", params.datasetId, "chats");
      const q = query(collectionRef, orderBy("createdAt", "desc"));
      const req = await getDocs(q);

      let allChats: any[] = [];
      req.forEach((doc) => {
        if (doc.exists()) {
          allChats.push({ ...doc.data(), chatId: doc.id });
        }
      });

      return allChats;
    } catch (e) {
      return e as any;
    }
  };
```
```tsx
const getUserChats = async ()<: Promise<Chat[]> => {...};
```
```tsx
const getUserChats = async ()<: Promise<Chat[]> => {...};

const { data } = useQuery<Chat[]>({  
  queryKey: ["getUserChats", user.id],
  queryFn: getUserChats,
});
```
```tsx
const getUserChats = async ()<: Promise<Chat[]> => {...};

const { data } = useQuery<Chat[]>({  
  queryKey: ["getUserChats", user.id],
  queryFn: getUserChats,
});


return (
  <div>
    {data.map((chat, index) => (
      <p key={index}>{chat.title}</p>
    ))}
  </div>
)
```
```tsx
const getUserChats = async ()<: Promise<Chat[]> => {...};

const { data, isLoading, isSuccess, isError, error } = useQuery<Chat[]>({  
  queryKey: ["getUserChats", user.id],
  queryFn: getUserChats,
});


return (
  <div>
    // state management
    {isLoading ? <Loader /> : null}
    {isSuccess && data.map((chat, index) => (
      <p key={index}>{chat.title}</p>
    ))}
    // error handling
    {isError && <p>Whoops! {error}</p>}
  </div>
)
```
````

---

# Beneficios
* <span v-click>No rerenders</span>
* <span v-click>Resultado guardado en cache</span>
* <span v-click>Data disponible de forma global (contexto)</span>
* <span v-click>Gestiona estados de request</span>
* <span v-click>Reintentos automáticos en caso de fallos</span>
* <span v-click>Minimiza solicitudes de red</span>
* <span v-click>Control sobre orden de disparo de peticiones</span>
* <span v-click>Soporte para React Suspense y Concurrent mode.</span>

<br>

<span v-click>

> Todos estos beneficios por solo usar nuevos hooks. No necesitamos reinventar la forma en la que trabajamos con firebase.
> 
</span>


---
layout: image-right
image: ./image.png
backgroundSize: contain
---


# Ejemplo más completo
Aquí hay varios elementos importantes que son fundamentales para controlar el *server state* a través de los Hooks que nos da la librería.


* QueryClient - Es nuestro react provider que se declara en `App.tsx` y que da contexto.
* basic hooks - useMutation (para POST) y useQuery (para GET)
* invalidateQueries - Se pasa el id el query que queremos invalidar y cuado se llame a la función se hace un refetch ✨

---

# Pasemos a dos ejemplos prácticos
### <span v-click>Exploración del Frida Stack</span>
* <span v-click> <span class="text-purple-400">Frida AI analytics</span>: Next.js, Shadcn, Tanstack Query</span>

<br> 

### <span v-click>Comparativa de resultados</span>
* <span v-click><span class="text-sky-300">Soy Tupperware App PWA</span>: React Router, Material UI</span>


---
layout: iframe-right
url: https://tkdodo.eu/blog/react-query-meets-react-router
---

# Data fetching no es lo mismo que data loading
React Router ahora es mucho más poderoso que antes. Muchas de las features que tenía el framework de Remix.js. Han pasado a ser de React Router.

> Fetching "as early as possible" is an important concept to provide the best possible user experience. Full Stack frameworks like NextJs or Remix move this step to the server, because that is the earliest entry point. With client rendered applications, we have no such luxury.

<br>

<span v-click>
No estamos aprovechando al máximo react router, haciendo fetching una vez se hizo el render de la página. ¡Debemos usar los Loaders!
</span>



---
layout: center
---

# Gracias
Built with Slidev

[Documentations](https://sli.dev) · [GitHub](https://github.com/slidevjs/slidev) · [Showcases](https://sli.dev/showcases.html)
