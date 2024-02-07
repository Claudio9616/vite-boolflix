<script>
import { store } from '../store';
export default {
    data: () => ({
        store
    }),
    emits: ['click-button']
}
</script>
<template>
    <button @click="$emit('click-button')"></button>
</template>
<style></style>