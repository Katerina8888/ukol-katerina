<template>
  <ul class="mt-2 lg:mt-[4rem] w-full mx-auto grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-1">
    <OneTask
      v-for="(task, index) in tasks"
      :key="index"
      :task="task"
      @remove-task="removeTask(index)"
    />
  </ul>
</template>

<script setup lang="ts">
import type { Task } from '../assets/types'
import OneTask from './OneTask.vue'

defineProps<{
  tasks: Task[]
}>()

const emit = defineEmits(['remove-task'])

const removeTask = (index: number) => {
  emit('remove-task', index)
}
</script>
