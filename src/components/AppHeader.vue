<script>
import AppForm from './AppForm.vue';
export default {
    name: 'AppHeader',
    components: { AppForm },
    emits: ['search-terms']
}
</script>
<template>
    <!-- sistemare logo -->
    <img src="https://tse2.mm.bing.net/th?id=OIP.7hBSuwqSw6Q6mTsXbdcBcgAAAA&pid=Api&P=0&h=180" alt="">
    <AppForm @search-movies-seires="$emit('search-terms', $event)" :placeHolder="'Inizia la ricerca'" :textButton="'CERCA'"
        class="text-end container my-4" />
</template>
<style lang="scss" scoped>
@use '../assets/stylesass/style.scss';

img {
    width: 200px;
}
</style>