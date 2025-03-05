<script setup>
const props = defineProps({
  title: String,
})
</script>

<template>
  <button class="button-primary w-full">{{ props.title }}</button>
</template>

<style scoped></style>
