<template>
    <div class="item">
        {{ props.title }}
        <button style="float: right; background-color: red" @click="$emit('deleteItem', props.index)">X</button>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps([
    'title', 'index'
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