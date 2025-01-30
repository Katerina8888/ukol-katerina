<!-- rozděl na více komponent -->
<template>
  <div class="md:mt-6 md:mx-6 px-12">
    <label v-if="label" :for="id" class="text-start block">{{ label }}</label>
    <input
      :type="type"
      :id="id"
      class="border border-white w-full bg-white"
      :placeholder="placeholder"
      :min="min"
      @input="$emit('input-changed', ($event.target as HTMLInputElement).value)"
    />
  </div>
</template>

<script setup lang="ts">
defineProps({
  type: {
    type: String,
    default: 'text',
  },
  id: {
    type: String,
    required: true,
  },
  label: {
    type: String,
    required: false,
  },
  placeholder: {
    type: String,
    default: '',
  },
  min: {
    type: Number,
    default: 1,
  },
})

defineEmits(['input-changed'])
</script>
