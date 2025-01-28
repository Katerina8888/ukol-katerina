<template>
  <form @submit.prevent="handleSubmit">
    <label for="newTask" class="sr-only">Task input</label>
    <input type="text" id="newTask" v-model="newTask" />
    <button type="submit">Add</button>
  </form>
</template>

<script setup lang="ts">
import { ref, defineEmits } from 'vue'

const emit = defineEmits<{
  (e: 'add-task', task: string): void
}>()

const newTask = ref('')

const handleSubmit = () => {
  if (newTask.value.trim() !== '') {
    emit('add-task', newTask.value)
    newTask.value = ''
  }
}
</script>

<style>
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
</style>
