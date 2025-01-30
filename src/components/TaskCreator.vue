<template>
  <div
    class="flex mx-auto md:mt-8 lg:mt-[8rem] justify-center text-center flex-col w-full md:w-1/2 lg:w-1/4 bg-katerina-600 font-bold py-8 rounded-md"
  >
    <h1>Task Manager</h1>

    <form ref="formRef" @submit.prevent="handleSubmit" class="relative flex flex-col">
      <InputComponent
        id="taskName"
        label="Task name"
        :value="taskInput"
        @input-changed="handleTaskInput"
      />
      <InputComponent
        id="taskHours"
        type="number"
        label="Hours to complete"
        :min="1"
        placeholder="1"
        :value="taskHours"
        @input-changed="handleTaskHours"
      />
      <ButtonAdd />
    </form>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import ButtonAdd from './ButtonAdd.vue'
import InputComponent from './InputComponent.vue'
import type { Task } from '../assets/types'

const taskInput = ref('')
const taskHours = ref(1)
const formRef = ref<HTMLFormElement | null>(null) // Reference na form

const emit = defineEmits<{
  (e: 'on-submit', task: Task): void
  (e: 'toggle-image'): void
}>()

const handleTaskInput = (input: string) => {
  taskInput.value = input
}

const handleTaskHours = (input: string) => {
  taskHours.value = Number(input) || 1
}

const handleSubmit = () => {
  if (taskInput.value.trim() === '') {
    alert('Please enter a valid task name and hours.')
    return
  }

  emit('on-submit', {
    name: taskInput.value,
    hours: taskHours.value,
    date: new Date().toLocaleDateString(),
  })

  emit('toggle-image')

  formRef.value?.reset()
  taskInput.value = ''
  taskHours.value = 1
}
</script>
