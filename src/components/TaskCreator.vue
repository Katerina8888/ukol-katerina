<template>
  <div
    class="flex mx-auto mt-[8rem] justify-center text-center flex-col w-1/4 bg-[#FCC6FF] font-bold py-8 rounded-md"
  >
    <!-- <form @submit.prevent="onSubmit"> -->
    <h1>Task Manager</h1>

    <form class="relative flex flex-col">
      <Input />
      <InputNumber />
      <Button>x</Button>
    </form>
  </div>
</template>

<script setup lang="ts">
import Input from './Input.vue'
import InputNumber from './InputNumber.vue'
import Button from './Button.vue'
</script>

<style>
.sr-only {
  clip: rect(0, 0, 0, 0);
}
</style>
