<template lang='pug'>
    div.o-background-image.u-overflow-auto
        h1.u-text-center
            span Galeria de Peliculas
        .c-filter
            .c-filter__btn.is--title
                span Filtrar por:
            button.c-filter__btn(v-on:click="OrderDate")
                span Fecha de lanzamiento
            button.c-filter__btn(v-on:click="OrderEpisode")
                span Numero de episodios
        .u-px3
            ul.o-grilla.c-container-cards
                li.c-container-cards__item(
                    v-for='film in films' :key="film.episode_id")
                    Card(:title='film.title' :release="new Date(film.release_date)" :episode="film.episode_id")
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
            fecha: new Date(),
            films: []
        }
    },
    created: async function() {
        let films = await axios.get('https://swapi.co/api/films/')
        this.films = films.data.results
        this.fecha = new Date(this.films[1].release_date) 
    },
    methods: {
        OrderDate () {
            // console.log('OrderDate')
            let ArraySort = function (films) {
                let temp = []
                temp = films.sort(function(a, b) {
                    a = new Date(a.release_date);
                    b = new Date(b.release_date);
                    return a>b ? -1 : a<b ? 1 : 0;
                })
                return temp
            }
            this.films = ArraySort(this.films)
        },
        OrderEpisode () {
            console.log('OrderEpisode')
            let ArraySort = function (films) {
                let temp = []
                temp = films.sort(function(a, b) {
                    if (a.episode_id >= b.episode_id){
                        return -1
                    } else {
                        return 1
                    }
                })
                return temp
            }
            this.films = ArraySort(this.films)
        }
    }
}
</script>

<style lang='stylus' scoped>
</style>