<script>
import { store } from '../store';
import CardsComponent from './CardsComponent.vue';
export default {
    name: 'AppMain',
    data: () => ({
        store
    }),
    components: { CardsComponent }
}
</script>
<template>
    <main class="container">
        <h2 class="mb-3">MOVIES</h2>
        <section class="d-flex row row-cols-2 row-cols-md-3 row-cols-lg-4 flex-wrap">
            <div v-for="movie in store.movies" :key="movie.id" class="col mb-4">
                <CardsComponent v-bind="movie" />
            </div>
        </section>
        <h2 class="mb-5">SERIES</h2>
        <section class="d-flex row row-cols-2 row-cols-md-3 row-cols-lg-4 flex-wrap">
            <div v-for="serie in store.series" :key="serie.id" class="col mb-4">
                <CardsComponent v-bind="serie" />
            </div>
        </section>
    </main>
</template>
<style lang="scss" scoped>
main {
    height: 100%;
}
</style>