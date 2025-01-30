<template>
  <ul class="mt-2 lg:mt-[4rem] w-full flex justify-center flex-wrap">
    <!-- TODO oddělit na samostatné komponenty -->
    <li
      v-for="(task, index) in tasks"
      :key="index"
      class="flex w-full md:w-1/2 lg:w-1/3 flex-col my-4"
    >
      <div class="w-5/6 md:w-1/2 bg-[#FCC6FF] mx-auto rounded-md p-2">
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

// DOTAZ: JAKÝ JE ROZDÍL V ZÁPISU CONST PROPS = DEFINE PROPS A ROVNOU DEFINE PROPS JAKO JE NÍŽE?
defineProps<{
  tasks: Task[]
}>()

const emit = defineEmits(['remove-task'])

const handleClick = (index: number) => {
  emit('remove-task', index) // Emitování kliknutí
}
</script>
