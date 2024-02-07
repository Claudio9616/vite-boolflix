<script>
export default {
    name: 'AppForm',
    data: () => ({
        searchText: ''
    }),
    emits: ['search-movies-seires']
}
</script>
<template>
    <form @submit.prevent.enter="$emit('search-movies-seires', searchText)">
        <input type="text" v-model.trim="searchText">
    </form>
</template>
<style></style>