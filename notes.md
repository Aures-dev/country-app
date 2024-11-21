## Utilisation de fetch

```js
const url = 'https://api.example.com/data'

function fetchApi() {
  try {
    return fetch(url) //on fetch () "recherche" les donnée grâce à l'url de l'api
      .then((res) => res.json()) //then nous aide à recup la donnée et la convertir en json
      .then(
        (data) => console.log(data) //then recup le json et l'affiche en console
      )
  } catch (error) {
    console.error(error) //si la requête échoue on affiche une erreur en console
  }
}
```
