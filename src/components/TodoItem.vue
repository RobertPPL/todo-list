<template>
    <div class="item">{{ props.title }}</div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps([
    'title'
]);

</script>

<style scoped>
 .item {
    padding: 10px;
    background-color: beige;
    /* max-width: 200px; */
    margin: 0;
 }
 .item:hover {
    background-color: aqua;
 }
</style>