<script setup>
import { ref } from 'vue';

const allCountry = ref([]);
const url = 'https://restcountries.com/v3.1/all';

// function fetchCountry() {
//     try {
//         return fetch(url)
//             .then((res) => res.json())
//             .then((data) => console.log(data)
//             );
//     } catch (error) {
//         console.error(error);
//     }
// }

async function fetchCountry() {
    const response = await fetch(url);
    allCountry.value = await response.json();
    console.log(allCountry.value);
}
fetchCountry();

const embleme = ref("embleme");
const indice = ref('0')
console.log(indice);


</script>

<template>
    <header>
        <!-- <h1>Republic of Benin</h1> -->
        <h1>{{ allCountry[indice]?.name.official }}</h1>
    </header>
    <!-- <img src="../assets/drapeau.png" alt="drapeau" class="drapeau"> -->
    <img :src="allCountry[indice]?.flags.png" alt="drapeau" class="drapeau">
    <main>
        <div class="country-list">
            Liste des pays
            <ul>
                <li v-for="(item, index) in allCountry" :key="index">
                    <a href="#" @click="() => (indice = allCountry.indexOf(item))">{{ item.name.official }}</a>
                </li>
            </ul>
        </div>
        <div class="main-grid">
            <article class="main-grid-item1">
                <p><span>Capitale: </span>{{ allCountry[indice]?.capital[0] }}</p>
                <!-- à rendre dynamique -->
                <p><span>Langue: </span>{{ allCountry[indice]?.languages.eng }}</p>
                <!-- <p><span>Monnaie: </span>{{  }}</p> -->
                <p><span>Continent: </span>{{ allCountry[indice]?.continents[0] }}</p>
                <p><span>Sous-région: </span>{{ allCountry[indice]?.subregion }}</p>
                <p><span>Emblème: </span> <img alt="emblème" :src="allCountry[indice]?.coatOfArms.png" :class="embleme">
                </p>
            </article>
            <article class="main-grid-item2">
                <p>Autres informations</p>
                <ul>
                    <li><span>Population: </span>{{ allCountry[indice]?.population }}</li>
                    <li>...</li>
                    <li>...</li>
                    <li>...</li>
                </ul>
            </article>
            <article class="main-grid-item3">
                <p>A propos</p>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Necessitatibus minima quia consequuntur. In
                    sapiente deleniti ipsa libero consequatur facilis eaque aliquid, assumenda reprehenderit cupiditate
                    reiciendis at voluptatem omnis placeat voluptatum qui blanditiis non, labore laboriosam. Nisi alias
                    quae facilis eum, quas cupiditate optio aspernatur quam saepe aperiam vitae perferendis! Ut,
                    suscipit id vitae quam nesciunt rem tempore nemo tenetur sed. Lorem ipsum dolor, sit amet
                    consectetur adipisicing elit. Dolore optio nam explicabo minus ab eveniet dolorum! Voluptatum soluta
                    voluptate doloremque? Facere modi aliquid nesciunt earum debitis voluptatibus ut culpa maiores.</p>
            </article>
        </div>
    </main>
    <footer></footer>
</template>

<style>
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    padding: 0;
    background-color: hsl(0deg 0% 94.12%);
    font-family: Arial, Helvetica, sans-serif;

    position: relative;
}

span {
    font-weight: bold;
}

header {
    background-image: linear-gradient(to right, hsl(122.42deg 40.08% 48.43%), hsl(123.2deg 84.27% 17.45%));
    height: 15em;
    color: white;

}

h1 {
    position: absolute;
    right: 5em;
    top: 3em;
}

main {
    display: flex;
    justify-content: space-between;
    background-color: hsl(0deg 0% 94.12%);
}

.drapeau {
    border-radius: 10px;
    position: absolute;
    top: 10em;
    left: 1em;
    height: 10em;
    width: 14%;
}

article {
    background-color: white;
    border-radius: 10px;
    padding: 1em;
    padding-top: 0;
}

.country-list {
    width: 20%;
    height: 50vh;
    padding: 1em;
    margin-top: 10em;
    margin-left: 0em;
    background-color: white;
    border-radius: 10px;

    overflow: scroll;
}

.main-grid {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(2, 1fr);
    gap: 1em;
    margin: 1em;
}

.main-grid-item1 {
    grid-column: 1/2;
}

.main-grid-item2 {
    grid-column: 2/3;
}

ul {
    list-style-type: none;
    padding-left: 0;
}

.main-grid-item3 {
    grid-column: 1/3;
}

a {
    text-decoration: none;
    font-weight: bold;
    color: black;
}

li {
    padding-block: 0.5em;
}

.embleme {
    width: 80%;
}
</style>