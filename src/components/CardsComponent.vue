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
    }
}
</script>
<template>
    <!-- sistemare layout, fare flag -->
    <div class="position-relative container qwe">
        <img :src="`https://image.tmdb.org/t/p/w342${img}`" alt="">
        <div class="position-absolute asd">
            {{ title }}
            {{ originalTitle }}
            {{ language }}
            {{ date }}
        </div>
    </div>
</template>
<style lang="scss" scoped>
@use '../assets/stylesass/style.scss';

.qwe {
    max-height: 250px;
}

img {
    max-width: 200px;
    display: block;
}

.asd {
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: chartreuse;
}
</style>