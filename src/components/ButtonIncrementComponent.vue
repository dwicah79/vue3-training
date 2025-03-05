<template>
  <div class="font-bold">Tombol Tambah</div>

  <button @click="increment" class="button-primary">+</button>
  {{ count }}
  <button @click="decrement" class="button-primary">-</button>
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
