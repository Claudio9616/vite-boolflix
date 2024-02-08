<script>
import AppForm from './AppForm.vue';
export default {
    name: 'AppHeader',
    components: { AppForm },
    emits: ['search-terms']
}
</script>
<template>
    <AppForm @search-movies-seires="$emit('search-terms', $event)" :placeHolder="'Inizia la ricerca'"
        :textButton="'CERCA'" />
</template>
<style></style>