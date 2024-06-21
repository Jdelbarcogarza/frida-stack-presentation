
# Data fetching en React

> *You can use an Effect to fetch data for your component. Note that if you use a framework, using your framework’s data fetching mechanism will be a lot more efficient than writing Effects manually.*
> 
> **-The React Team**

<br>

### **¿Cómo se comporta un fetch dentro de useEffect?**
Esto es lo que sucede realmente en un primer render

1. <span v-click>Primero se cargará el HTML de la ruta que visitamos</span>
2. <span v-click>Luego se descargará todo el JavaScript que necesita esa página</span>
3. <span v-click>Se renderiza la app (Recordemos react necesita JS)</span>

<span v-click>*oh no* El cliente se da cuenta que debe hacer un fetch para traer la información para que funcione la app!!</span>

4. <span v-click>Hacer el fetch a la API para traer la información</span>
5. <span v-click>(extra) actualizar estado para mostrar datos en la app</span>

<!-- 
Puedes usar useEffect para hacer data fetching en tu componente. Pero es importante recalcar que si utilizas un framework, el mecanismo de data fetching será mucho más eficiente que escrbir useEffects manualmente -->

---
transition: slide-up
layout: image-right
image: /images/network_waterfall.png
backgroundSize: contain
---

# Data fetching en React
(continue...)

El comportamiento anterior es "lento" porque todo se hace del lado del cliente y corre en la computadora del usuario, no del lado del servidor.

Otros "caveats" que tiene el `useEffect` son:
1. *network waterfalls* (ver imágen)
<!-- recalcar que en la imágen las API calls son lo último que se "manda a llamar" -->
2. Los useEffects no hacen un *preload* ni hacen *data caching*
3. Race conditions

<br>

<span v-click>

Escribir un `useEffect` que hace data fetching y no sufra de estos problemas es complicado y tedioso (mala DX) y NO ES NECESARIO.

</span>



---
transition: slide-left
layout: image-right
image: /images/spa_ssr_streaming.jpeg
backgroundSize: contain
---

# SSR y Streaming

<br>

Con todo lo que conlleva hacer un request en una SPA, los nuevos paradigmas han incluso minimizado o desaparecido desventajas que por naturaleza tienen las full client-side apps.

