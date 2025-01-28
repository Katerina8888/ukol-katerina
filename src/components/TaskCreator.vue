<template>
  <div>
    <Input v-model:taskInput="newTask" @addTask="addTask" />
    <Task :tasks="tasks" @deleteTask="deleteTask" />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Input from './Input.vue'
import Task from './Task.vue'

const tasks = ref<string[]>([])
const newTask = ref('')

const addTask = (task: string) => {
  tasks.value.push(task)
}

const deleteTask = (index: number) => {
  tasks.value.splice(index, 1)
}
</script>
