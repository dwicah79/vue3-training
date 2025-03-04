<template>
  <div>
    <h1>{{ name }}</h1>
    <button @click="showName">Tampilkan Nama Di Console</button>
  </div>
</template>

<script setup>
const name = 'Dwi Cahyo Nugroho'

const showName = () => {
  console.log(name)
}
</script>
