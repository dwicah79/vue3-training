<script setup>
import MainButton from './components/MainButton.vue'
import OptionComponent from './components/OptionComponent.vue'
import CompositionComponent from './components/CompositionComponent.vue'
import ButtonIncrementComponent from './components/ButtonIncrementComponent.vue'
</script>

<template>
  <MainButton :title="`Submit`" />
  <MainButton :title="`Log In`" />
  <MainButton :title="`Kirim`" />

  <OptionComponent />
  <CompositionComponent />
  <ButtonIncrementComponent />
</template>

<style scoped></style>
