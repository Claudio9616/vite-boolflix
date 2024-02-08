<script>
export default {
    name: 'Card Components',
    props: {
        id: Number,
        title: String,
        originalTitle: String,
        language: String,
        vote: Number,
        text: String,
        date: String,
        img: String
    },
    computed: {
        flags() {
            const flags = ['it', 'en']
            return flags.includes(this.language)
        },
        flagSrc() {
            const url = new URL(`../assets/img/${this.language}.png`, import.meta.url)
            return url.href
        }
    }
}
</script>
<template>
    <!-- sistemare layout -->
    <div class="position-relative container">
        <img v-if="img" :src="`https://image.tmdb.org/t/p/w342${img}`" alt="">
        <img v-else src="https://tse3.mm.bing.net/th?id=OIF.n2ItAAPqGWNyi5sl%2bPu2cw&pid=Api&P=0&h=180" alt=""
            class="myImg">
        <div class="asd">
            {{ title }}
            {{ originalTitle }}
            {{ language }}
            <img v-if="flags" :src="flagSrc" :alt="language">
            <span v-else>{{ language }}</span>
            {{ date }}
        </div>
    </div>
</template>
<style lang="scss" scoped>
@use '../assets/stylesass/style.scss';

img {
    max-height: 250px;
    display: block;
}

.myImg {
    height: 150px;
}

.asd {
    display: none;
    position: absolute;
    height: 100%;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: white;
}

.asd img {
    width: 50px;
}

.asd:hover {
    display: block;
    cursor: pointer;
}
</style>