<template>
    <div class="hero">
        <v-carousel
            cycle
            progress
            interval="10000"
            height="450"
            hide-delimiters
            show-arrows-on-hover
        >
            <v-carousel-item
            v-for="(image, i) in images"
            :key="i"
            :src="image.src"
            >
                <h1 class="carousel-title">{{ image.title }}</h1>
            </v-carousel-item>
        </v-carousel>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                images: [
                    {src: require('../assets/kyoto.jpg'), title: 'Kyoto'},
                    {src: require('../assets/nagoya.jpg'), title: 'Nagoya'},
                    {src: require('../assets/osaka.jpg'), title: 'Osaka'},
                    {src: require('../assets/sapporo.jpg'), title: 'Sapporo'},
                    {src: require('../assets/tokyo.jpg'), title: 'Tokyo'},
                    {src: require('../assets/yokohama.jpg'), title: 'Yokohama'},
                ],
            }
        },
    }
</script>

<style lang="scss" scoped>
    .hero {
        height: 100%;
    }
    .carousel-title {
        position: absolute;
        bottom: 20px;
        right: 40px;
        color: #fff;
    }
</style>