<template>
  <ul>
    <li v-for="(task, index) in tasks" :key="index">
      <span>{{ task }}</span>
      <button @click="handleDelete(index)">x</button>
    </li>
  </ul>
</template>

<script setup lang="ts">
import { defineProps, defineEmits } from 'vue'

defineProps<{
  tasks: string[]
}>()

const emit = defineEmits<{
  (e: 'delete-task', index: number): void
}>()

const handleDelete = (index: number) => {
  emit('delete-task', index)
}
</script>
