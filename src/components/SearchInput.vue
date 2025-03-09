<template>
  <div
    class="relative w-full max-w-md flex items-center border border-gray-300 rounded-lg overflow-hidden shadow-sm"
  >
    <input
      v-model="query"
      type="text"
      placeholder="Cari buku yang anda inginkan"
      class="w-full px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
    />
    <button
      v-if="query"
      @click="clearSearch"
      class="absolute right-16 inset-y-0 flex items-center px-2 text-gray-500 hover:text-gray-700"
    >
      ✕
    </button>
    <button
      @click.prevent="$emit('search', { query: query })"
      class="bg-blue-500 text-white px-4 py-2 hover:bg-blue-600"
    >
      Cari
    </button>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  setup(_, { emit }) {
    const query = ref('')
    const clearSearch = () => {
      query.value = ''
    }
    return { query, clearSearch }
  },
}
</script>
