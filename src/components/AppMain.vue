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
    <main class="container my-5">
        <h2 class="mb-3">MOVIES</h2>
        <div class="border rounded-2 border-2 border-black d-flex g-4 row row-cols-2 row-cols-md-3 row-cols-lg-4">
            <div v-for="movie in store.movies" :key="movie.id" class="col">
                <CardsComponent v-bind="movie" />
            </div>
            <h2 class="mb-3">SERIES</h2>
            <div v-for="serie in store.series" :key="serie.id" class="col">
                <CardsComponent v-bind="serie" />
            </div>
        </div>
    </main>
</template>
<style lang="scss" scoped></style>