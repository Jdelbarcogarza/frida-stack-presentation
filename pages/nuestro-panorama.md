
# ¿Cómo se ven nuestros *useEffect*?
En varios proyectos tenemos este mismo patrón de una u otra forma.


```ts 
function Bookmarks({ category }) {
  const [data, setData] = useState([])
  const [error, setError] = useState()

  useEffect(() => {
    fetch(`${endpoint}/${category}`)
      .then(res => res.json())
      .then(d => setData(d))
      .catch(e => setError(e))
  }, [category])

  // Return JSX based on data and error state
}
```
[Veamos como resolvemos](https://tkdodo.eu/blog/why-you-want-react-query)


