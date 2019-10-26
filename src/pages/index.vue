<template lang='pug'>
    div.o-background-image.u-overflow-auto
      h1.u-text-center
          span MVP PELICULAS
      .u-px3
        ul.o-grilla.c-container-cards
          li.c-container-cards__item()
            nuxt-link(:to="`/peliculas`")
              card(title='Peliculas')
          li.c-container-cards__item()
            nuxt-link(:to="`/personajes`")
              card(title='Personajes')
</template>

<script>
  import Card from '../components/Card'
  export default {
    name: 'Inicio',
    components: {
      Card
    }
  }
</script>

<style lang='stylus' scoped>
</style>