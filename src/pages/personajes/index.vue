<template lang='pug'>
    div.o-background-image.u-overflow-auto
      h1.u-text-center
        span Galeria de Personajes
      .u-px3
        ul.o-grilla.c-container-cards
          li.c-container-cards__item(
            v-for='person in people' :key="person.created")
            nuxt-link(:to="`/personajes/${person.url.substring(28,person.url.length-1)}`")
              Card(:title='person.name' :release="new Date(person.created)" :episode="person.films.length")
        btn-float(url="/")
</template>

<script>
  import axios from 'axios'
  import Card from '../../components/Card'
  import BtnFloat from '../../components/Btn-float'
  export default {
    name: 'Personajes',
    components: {
        Card, BtnFloat
    },
    data() {
        return {
            people: [{
              name:'', url:'', created:'', films:[]
            }]
        }
    },
    created: async function() {
        let people = await axios.get('https://swapi.co/api/people/')
        this.people = people.data.results
    }
  }
</script>

<style lang='stylus' scoped>
</style>