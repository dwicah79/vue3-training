<script>
export default {
  data() {
    return {
      name: 'Dwi Cahyo Nugroho',
    }
  },
  methods: {
    showName() {
      console.log(this.name)
    },
  },
}
</script>

<template>
  <div>
    <h1>{{ name }}</h1>
    <button @click="showName">Tampilkan Nama Di Console</button>
  </div>
</template>
