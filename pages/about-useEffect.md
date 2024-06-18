# Qué es useEffect

es un Hook de React utilizado para sincronizar componentes con **sistemas externos**. Un Effect permite ejecutar código después de que este se haya renderizado, para que se puedan sincronizar tu código, y un sistema fuera de React.

> *"El useEffect es como una puerta que te perimte salir de lo que es react para que ejecutar código fuera de este."*



<br>

Crearemos un custom hook llamado `useIsMounted()` y lo utilizaremos en una página llamada `/page.tsx`:
```ts
const isMounted = useIsMounted()
```

---
---

# Ejemplo


Aquí es donde creamos nuestro custom hook `/hooks/useIsMounted.tsx`


```ts {all|4|5-12}
import { useCallback, useEffect, useRef } from 'react'

export function useIsMounted(): () => boolean {
  const isMounted = useRef(false)

  useEffect(() => {
    isMounted.current = true

    return () => {
      isMounted.current = false
    }
  }, [])

  return useCallback(() => isMounted.current, [])
}
```

<span v-click=1>

* Un useRef igual es una forma en la que react permite que el código hable directamente con el nodo dentro del Virtual DOM Tree

</span>

<span v-click=2>

* El useEffect está hablando con el nodo del DOM (sistema fuera de react y su *estado*)

</span>

