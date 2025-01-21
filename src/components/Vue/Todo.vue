<script setup>
import { todoList } from '../../data/todoList';
import { ref } from 'vue';

const listRef = ref(todoList);
const tickedListsRef = ref([]);
    
const taskDone = (item) =>{
    listRef.value = listRef.value.filter((list) => list !== item);
    tickedListsRef.value = [...tickedListsRef.value,item];
}

const taskUndone = (item) =>{
    tickedListsRef.value = tickedListsRef.value.filter((list) => list !== item);
    listRef.value = [...listRef.value,item];
}
</script>
<template>
    <section class="todo-list">
        <div class="container">
            <div class="todo-flex" v-for="(item) in listRef" :key="item.id">
                <input type="checkbox" @click="taskDone(item)"/>
                <h1> {{ item.taskName }} </h1>
            </div>
            <h1> This is the completed tasks : </h1>
            <div class="todo-flex" v-for="(item) in tickedListsRef" :key="item.id">
                <input type="checkbox" @click="taskUndone(item)"/>
                <h1> {{item.taskName}} </h1>
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