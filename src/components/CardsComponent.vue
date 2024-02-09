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
        }
    }
}
</script>
<template>
    <div class="position-relative hover">
        <img v-if="img" :src="`https://image.tmdb.org/t/p/w342${img}`" alt="" class="asd">
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
            <!-- mettere stelline -->
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

.hover:hover {
    cursor: pointer;
    overflow-y: auto;
    overflow-x: hidden;
    background-color: black;

    ul {
        display: inline-block;
    }

    .asd,
    .myImg {
        filter: brightness(0.2);
    }
}
</style>