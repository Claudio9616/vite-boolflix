<script>
import AppForm from './AppForm.vue';
export default {
    name: 'AppHeader',
    components: { AppForm },
    emits: ['search-terms']
}
</script>
<template>
    <header class="d-flex align-items-center">
        <h1 class="ms-2 text-white">BOOLFIX</h1>
        <AppForm @search-movies-seires="$emit('search-terms', $event)" :placeHolder="'Inizia la ricerca'"
            :textButton="'CERCA'" class="text-end container my-4" />
    </header>
</template>
<style lang="scss" scoped>
header {
    box-shadow: 0 10px 20px;
}
</style>