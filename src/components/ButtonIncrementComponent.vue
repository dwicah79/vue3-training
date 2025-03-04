<template>
  <div>Tombol Tambah</div>

  <button @click="increment">+</button>
  {{ count }}
  <button @click="decrement">-</button>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
    }
  },
  methods: {
    increment() {
      this.count++
    },
    decrement() {
      this.count--
    },
  },
}
</script>
