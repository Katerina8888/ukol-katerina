<template>
  <li class="flex-col my-4">
    <div class="w-5/6 bg-katerina-600 mx-auto rounded-md p-2">
      <div class="flex justify-between">
        <div>{{ task.hours }}h</div>
        <h2 class="font-bold">{{ task.name }}</h2>
        <ButtonRemove label="X" @click="handleClick()" />
      </div>

      <div class="text-center">{{ task.date }}</div>
    </div>
  </li>
</template>

<script setup lang="ts">
import ButtonRemove from './ButtonRemove.vue'
import type { Task } from '../assets/types'

defineProps<{
  task: Task
}>()

const emit = defineEmits(['remove-task'])

const handleClick = () => {
  emit('remove-task')
}
</script>
