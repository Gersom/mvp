<template lang='pug'>
    .c-card
        figure
            img(:src="this.miniature")
        h5
            |this.title
</template>

<script>
    import axios from 'axios'
    export default {
        name: 'Card',
        props: {
            title: {
                type: String,
                default: '---',
                required: true
            },
            miniature: {
                type: String,
                default: 'https://picsum.photos/300/300',
                required: false
            }
        }
    }
</script>

<style lang='stylus' scoped>
</style>