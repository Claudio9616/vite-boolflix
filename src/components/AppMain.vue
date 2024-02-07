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
        <div class="border rounded-2 border-2 border-black d-flex g-4 row row-cols-2 row-cols-md-3 row-cols-lg-5">
            <div v-for="movie in store.movies" :key="movie.id" class="col">
                <CardsComponent v-bind="pokemon" />
            </div>
        </div>
    </main>
</template>
<style lang="scss" scoped></style>