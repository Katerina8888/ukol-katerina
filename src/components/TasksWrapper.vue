<template>
  <ul class="mt-2 lg:mt-[4rem] w-full mx-auto grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-1">
    <!-- TODO oddělit na samostatné komponenty -->
    <li v-for="(task, index) in tasks" :key="index" class="flex-col my-4">
      <div class="w-5/6 bg-katerina-600 mx-auto rounded-md p-2">
        <div class="flex justify-between">
          <div>{{ task.hours }}h</div>
          <h2 class="font-bold">{{ task.name }}</h2>
          <ButtonRemove label="X" @click="handleClick(index)" />
        </div>

        <div class="text-center">{{ task.date }}</div>
      </div>
    </li>
  </ul>
</template>

<script setup lang="ts">
import ButtonRemove from './ButtonRemove.vue'
import type { Task } from '../assets/types'

defineProps<{
  tasks: Task[]
}>()

const emit = defineEmits(['remove-task'])

const handleClick = (index: number) => {
  emit('remove-task', index)
}
</script>
