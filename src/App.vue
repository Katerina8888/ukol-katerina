<template>
  <div id="app" class="relative">
    <TaskCreator @on-submit="addTask" @toggle-image="toggleImage" />
    <TasksWrapper :tasks="tasks" @remove-task="removeTask" />
    <CatImages :showFirstImage="showFirstImage" />
  </div>
</template>

<script setup lang="ts">
import TaskCreator from './components/TaskCreator.vue'
import TasksWrapper from './components/TasksWrapper.vue'
import CatImages from './components/CatImages.vue'
import { ref } from 'vue'
import type { Task } from './assets/types'

const tasks = ref([] as Task[])
const showFirstImage = ref(true)

const addTask = (task: Task) => {
  tasks.value.push(task)
  console.log(tasks.value)
}

const removeTask = (index: number) => {
  tasks.value.splice(index, 1)
  console.log(tasks.value)
}

const toggleImage = () => {
  showFirstImage.value = !showFirstImage.value
}
</script>
