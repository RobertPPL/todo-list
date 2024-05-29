<template>
  <div class="list">
    <button @click="addItem" class="btn btn-primary">Add new item</button>
    <input type="text" v-model="newItemName" class="form-control" />
    <ul style="padding: 0; padding: 0;">
      <TodoItem v-for="(item, index) in itemList" :key="index" :title="item" :index="index" @delete-item="deleteItem" />
    </ul>
    <h2 v-if="itemList.length === 0">No items...</h2>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import TodoItem from './TodoItem.vue';

let newItemName = ref('');
let itemList = ref([]);
let localList = localStorage.getItem('localList');
if(localList) {
  itemList.value = localList.split(',');
}


const addItem = function () {
  if (newItemName.value.trim().length === 0) {
    return;
  }

  itemList.value.push(newItemName.value.trim());
  localStorage.setItem('localList', itemList.value)
  newItemName.value = '';
}

const deleteItem = function(index) {
  itemList.value.splice(index, 1);
  localStorage.setItem('localList', itemList.value)
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.btn {
  padding: 5px;
  border: 1px solid silver;
  border-radius: 5px;
}

.btn-primary {
  background-color: dodgerblue;
}

.form-control {
  padding: 5px;
  border: 1px solid silver;
  border-radius: 5px;
}

.list {
  padding: 10px;
  border: 1px solid black;
  max-width: 400px;
  margin: 0 auto;
}
</style>
