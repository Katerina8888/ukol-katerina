<template>
  <div id="app">
    <TaskCreator @on-submit="addTask" />
    <TasksWrapper :tasks="tasks" @remove-task="removeTask" />
  </div>
</template>

<script setup lang="ts">
import TaskCreator from './components/TaskCreator.vue'
import TasksWrapper from './components/TasksWrapper.vue'
import { ref } from 'vue'
import type { Task } from './assets/types'

const tasks = ref([] as Task[])

const addTask = (task: Task) => {
  tasks.value.push(task)
  console.log(tasks.value)
}

const removeTask = (index: number) => {
  tasks.value.splice(index, 1)
  console.log(tasks.value)
}
</script>
