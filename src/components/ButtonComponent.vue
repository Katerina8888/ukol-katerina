<template>
  <button
    :class="buttonClasses"
    class="rounded-md text-center hover:transition-all hover:duration-500 hover:cursor-pointer"
  >
    {{ label }}
  </button>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue'

export default defineComponent({
  props: {
    variant: {
      type: String as () => 'default' | 'dismiss',
      default: 'default',
    },
    label: {
      type: String,
      required: true,
      default: '',
    },
  },
  setup(props) {
    const buttonClasses = computed(() => {
      return props.variant === 'dismiss'
        ? 'w-4 h-4 text-xs bg-black text-white hover:text-black hover:bg-white'
        : 'w-16 h-8 bg-black text-white mx-auto my-4 hover:text-black hover:bg-white'
    })

    return { buttonClasses }
  },
})
</script>
