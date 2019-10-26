<template lang='pug'>
    div.u-overflow-auto
        h1
            span Galeria de Peliculas
        ul.c-container-cards.o-grilla
            li.c-container-cards__item(
                v-for='film in films' :key="film.episode_id")
                Card(:title='film.title')
</template>

<script>
import axios from 'axios'
import Card from '../../components/Card'
export default {
    name: 'Peliculas',
    components: {
        Card
    },
    data() {
        return {
            films: []
        }
    },
    created: async function() {
        let films = await axios.get('https://swapi.co/api/films/')
        this.films = films.data.results
    }
}
</script>

<style lang='stylus' scoped>
</style>