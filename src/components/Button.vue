<script setup lang="ts">
// defineProps({
//   label: {
//     type: String,
//     required: true
//   }
// })
</script>

<template>
  <button class="px-4 p-1 bg-amber-600 hover:bg-amber-500 transition-colors duration-100 rounded">
    <slot/>
  </button>
</template>

<style scoped>

</style>