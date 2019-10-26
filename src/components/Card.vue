<template lang='pug'>
    .c-card.u-bg-secondary
        .c-card__date.z-index-3(
            :class="this.fecha=='' ? 'u-display-none' : ''")
            span {{this.fecha}}
        figure.u-position-relative.z-index-1
            img(:src="this.miniature")
        h5.c-card__title(
            class="u-uppercase u-bg-secondary u-position-relative z-index-2 u-text-center u-font-size--0-75rem u-margin-bottom-0 u-margin-top-0 u-padding-top-bottom"
        )
            span {{this.title}} </br>
            span(:class="this.episode==0 ? 'u-display-none' : ''") ({{this.episode}})
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
            release: {
                type: [Date, String],
                default: '',
                required: false
            },
            episode: {
                type: Number,
                default: 0,
                required: false
            },
            miniature: {
                type: String,
                default: 'https://picsum.photos/300/300',
                required: false
            }
        },
        data() {
            return {
                hover: false
            }
        },
        computed: {
            fecha () {
                if(this.release !== ''){
                    let temp = this.release.getDate() + "/" + (this.release.getMonth() +1) + "/" + this.release.getFullYear()
                    return temp
                } else {
                    return ''
                }
            }
        }
    }
</script>

<style lang='stylus' scoped>
</style>