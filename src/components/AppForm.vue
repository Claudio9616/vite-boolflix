<script>
export default {
    name: 'AppForm',
    data: () => ({
        searchText: ''
    }),
    emits: ['search-movies-seires'],
    props: {
        textButton: String,
        placeHolder: String
    }
}
</script>
<template>
    <form @submit.prevent="$emit('search-movies-seires', searchText)">
        <input type="text" v-model.trim="searchText" :placeholder="placeHolder">
        <button>{{ textButton }}</button>
    </form>
</template>
<style></style>