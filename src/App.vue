<template>
  <div id="app">
    <TaskCreator @on-submit="addTask" />
    <TasksWrapper :tasks="tasks" @click="removeTask" />
  </div>
</template>

<script setup lang="ts">
import TaskCreator from './components/TaskCreator.vue'
import TasksWrapper from './components/TasksWrapper.vue'
import { ref } from 'vue'
import type { Task } from './assets/types'

const tasks = ref([] as Task[]) // Uchovávání seznamu úkolů

const addTask = (task: Task) => {
  tasks.value.push(task)
  console.log(tasks.value)
  // DOTAZ: JAK V KONZOLI ODSTRANIT TY PROXY, ABYCH MĚLA ROVNOU VYPSANÉ POLE?
}

const removeTask = () => {
  // tasks.value.pop()
  console.log(tasks.value)
}
</script>
