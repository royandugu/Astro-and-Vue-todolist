<script setup>
import { todoList } from '../../data/todoList';
import { ref } from 'vue';

const listRef = ref(todoList);
    
const taskDone = (item) =>{
    listRef.value = listRef.value.filter((list) => list !== item);
}
</script>
<template>
    <section class="todo-list">
        <div class="container">
            <div class="todo-flex" v-for="(item) in listRef" :key="item.id">
                <input type="checkbox" @click="taskDone(item)"/>
                <h1> {{ item.taskName }} </h1>
            </div>
        </div>
    </section>
</template>
<style>
.todo-flex {
    display: flex;
    gap: 12px;
}

input {
    cursor: pointer;
}
</style>