<template>
  <div
    class="flex flex-col rounded-lg shadow-lg hover:shadow-2xl transition-shadow duration-300 overflow-hidden bg-white"
  >
    <slot name="header" />
    <div class="p-6">
      <slot name="content" />
    </div>
  </div>
</template>

<script setup>
// Script setup untuk BookCards
</script>
