
## Web dev en 2024

Sí hablar de esto y estructurarlo bien, porque se pueden dar más pláticas derivadas de esta.

- [ ] Enlistar todos los temas recientes

### Qué es useEffect

Hook de React utilizado para sincronizar componentes con **sistemas externos**. Un Effect permite ejecutar código después de que este se haya renderizado, para que se puedan sincronizar tu código, y un sistema fuera de React.

"Vean el useEffect como una ventana que te saca de lo que es react, y te permite ejecutar código fuera de este"

Un ejemplo de cómo utilizar useEffect para sincronizar algo **fuera** de React:

Crear un custom hook llamado `useIsMounted()`

Así lo utilizamos `/page.tsx`:
```ts
const isMounted = useIsMounted()
```


`/hooks/useIsMounted.tsx`
```ts
import { useCallback, useEffect, useRef } from 'react'

export function useIsMounted(): () => boolean {
  /* un useRef igual es una forma en la que react permite que el developer
   hable directamente con el nodo dentro del DOM Tree */
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

### Data fetching en React


### Hook libraries

> Recuerden no reinventar la rueda!

Utilicen estas librerías ya probadas y hechas por expertos para desarrollar sus aplicaciones

* usehooks-ts - fully open source. Copy-paste hooks
* @ui.dev/usehooks - hooks como paquete.


