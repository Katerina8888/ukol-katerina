<template>
  <li class="flex w-full md:w-1/2 lg:w-1/3 flex-col my-4">
    <div class="w-5/6 md:w-1/2 bg-katerina-600 mx-auto rounded-md p-2">
      <div class="flex justify-between">
        <div>{{ task.hours }}h</div>
        <h2 class="font-bold">{{ task.name }}</h2>
        <ButtonRemove
          label="X"
          variant="dismiss"
          @click="handleDismiss"
          @updateLabel="onUpdateLabel"
        />
      </div>

      <div class="text-center">{{ task.date }}</div>
    </div>
  </li>
</template>

<script setup lang="ts">
import { defineProps } from 'vue'
import ButtonRemove from './ButtonRemove.vue'

defineProps({
  task: {
    type: Object,
    required: true,
  },
})

const emit = defineEmits<{
  (e: 'updateLabel', label: string): void
}>()

const handleDismiss = () => {
  console.log('Kliknuto na tlačítko X')
  emit('updateLabel', 'X') // Emitování hodnoty 'X' rodiči (App.vue)
}

const onUpdateLabel = (label: string) => {
  console.log('Label update:', label) // Můžeš sem přidat logiku pro aktualizaci
}
</script>
