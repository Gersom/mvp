<template lang='pug'>
    .c-btn-float
        nuxt-link(:to="this.url")
            span > Regresar
</template>
<script>
export default {
    props: {
        url: {
            type: String,
            default: '---',
            required: true
        }
    }
}
</script>
<style lang='stylus' scoped>

</style>