<template lang='pug'>
  div.o-background-image.u-overflow-auto
    h1.u-text-center
      span {{this.person.url}}

    ul.c-show-data
      li.c-show-data__item
        span Nombre:
        span {{this.person.name}}
      li.c-show-data__item
        span Peso:
        span {{this.person.mass}}Kg
      li.c-show-data__item
        span Color de ojos:
        span {{this.person.eye_color}}
      li.c-show-data__item
        span Genero:
        span {{this.person.gender}}
      li.c-show-data__item
        span Altura:
        span {{this.person.height}}
      li.c-show-data__item
        span Trabajo:
        span {{this.person.homeworld}}
      li.c-show-data__item
        span Color de ropa:
        span {{this.person.skin_color}}
      li.c-show-data__item
        span Peliculas:
        span {{this.person.films.length}}
      li.c-show-data__item
        span Vehiculos:
        span {{this.person.vehicles.length}}

    btn-float(url="/personajes")
</template>

<script>
  import axios from 'axios'
  import BtnFloat from '../../../components/Btn-float'
  export default {
    name: 'PersonajeId',
    components: {
      BtnFloat
    },
    data (){
      return{
        person: {
          name:'', mass:'', url: '', eye_color:'', gender:'', height:'', homeworld:'', skin_color: '', films:[], vehicles:[]
        }
      }
    },
    created: async function() {
      let person = await axios.get(`https://swapi.co/api/people/${this.$route.params.id}`)
      this.person = person.data
    },
  }
</script>

<style lang='stylus' scoped>
</style>