<template lang='pug'>
    div.o-background-image.u-overflow-auto
        h1.u-text-center
            span {{this.film.url}}

        ul.c-show-data
          li.c-show-data__item
            span Título:
            span {{this.film.title}}
          li.c-show-data__item
            span Director:
            span {{this.film.director}}
          li.c-show-data__item
            span Productor:
            span {{this.film.producer}}
          li.c-show-data__item
            span Episodio:
            span {{this.film.episode_id}}
          li.c-show-data__item
            span Rastreo de apertura:
            span {{this.film.opening_crawl}}
          li.c-show-data__item
            span Rastreo de apertura:
            span {{this.film.opening_crawl}}
          li.c-show-data__item
            span Especies:
            span {{this.film.species.length}}
          li.c-show-data__item
            span Personajes:
            span {{this.film.characters.length}}

        btn-float(url="/peliculas")
</template>

<script>
  import axios from 'axios'
  import BtnFloat from '../../../components/Btn-float'
  export default {
    name: 'PeliculaId',
    components: {
      BtnFloat
    },
    data (){
      return{
        film: {
          title: '---',
          director: '---',
          producer: '---',
          episode_id: '0',
          opening_crawl: '',
          species:[],
          characters:[]
        }
      }
    },
    created: async function() {
      let film = await axios.get(`https://swapi.co/api/films/${this.$route.params.id}`)
      this.film = film.data
    },
  }
</script>

<style lang='stylus' scoped>
</style>