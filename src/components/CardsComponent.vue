<script>
export default {
    name: 'Card Components',
    props: {
        id: Number,
        title: String,
        originalTitle: String,
        language: String,
        vote: Number,
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
        },
        votes() {
            return Math.ceil(this.vote / 2)
        }
    }
}
</script>
<template>
    <div class="position-relative card-container">
        <img v-if="img" :src="`https://image.tmdb.org/t/p/w342${img}`" alt="" class="img-production">
        <img v-else src="https://tse3.mm.bing.net/th?id=OIF.n2ItAAPqGWNyi5sl%2bPu2cw&pid=Api&P=0&h=180" alt=""
            class="myImg">
        <ul class="text-center">
            <li>{{ title }}</li>
            <li>{{ originalTitle }}</li>
            <li>{{ language }}</li>
            <li>
                <img v-if="flags" :src="flagSrc" :alt="language">
                <span v-else>{{ language }}</span>
            </li>
            <li>
                <i v-for="n in 5" :key="n" class="fa-star" :class="n <= votes ? 'fa-solid' : 'fa-regular'"></i>
            </li>
        </ul>
    </div>
</template>
<style lang="scss" scoped>
@use '../assets/stylesass/style.scss';

img {
    max-width: 100%;
}

ul {
    display: none;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    padding: 0;
    margin: 0;
    list-style-type: none;
    color: white;
}

li img {
    max-width: 100px;
}

.fa-star {
    color: yellow;
}

.card-container:hover {
    cursor: pointer;
    overflow-y: auto;
    overflow-x: hidden;
    background-color: black;

    ul {
        display: inline-block;
    }

    .img-production,
    .myImg {
        filter: brightness(0.2);
    }
}
</style>