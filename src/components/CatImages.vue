<template>
  <!-- jsem si vědoma nekvality obrázků, ale nechtěla jsem se víc zdržovat :) -->
  <div
    class="hidden md:block md:w-[130px] md:h-[130px] lg:w-[200px] lg:h-[200px] xl:w-[300px] xl:h-[300px] mt-4 absolute right-[3rem] top-[10%]"
  >
    <img
      v-if="showFirstImage"
      src="../assets/cat3.webp"
      alt="Cat 1"
      loading="lazy"
      width="300"
      height="300"
      class="max-w-[100%] h-auto"
    />
    <img
      v-else
      src="../assets/cat4.gif"
      alt="Cat 2"
      loading="lazy"
      width="300"
      height="300"
      class="max-w-[100%] h-auto"
    />
  </div>
</template>

<script setup lang="ts">
defineProps<{
  showFirstImage: boolean
}>()
</script>
