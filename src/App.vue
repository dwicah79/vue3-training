<script setup>
import SearchInput from './components/SearchInput.vue'
import BookCards from './components/BookCards.vue'
import { ref } from 'vue'

const book = ref({ items: [], totalItems: 0 })

async function search({ query }) {
  if (!query) return

  try {
    const url = new URL(import.meta.env.VITE_BASE_URL)
    url.searchParams.set('q', query)

    const response = await fetch(url)

    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`)
    }

    const data = await response.json()

    if (!data.items) {
      throw new Error('No items found in the response')
    }

    book.value = { items: data.items, totalItems: data.totalItems }
  } catch (error) {
    console.error('Gagal mengambil data:', error)
    book.value = { items: [], totalItems: 0 }
  }
}
</script>

<template>
  <div class="container mx-auto px-6 py-12">
    <h1 class="font-extrabold text-5xl text-center text-gray-900 mb-8">
      Cari Buku Yang Anda Inginkan
    </h1>
    <div class="flex justify-center mb-12">
      <SearchInput @search="search" class="w-full max-w-lg" />
    </div>

    <section>
      <h2 v-if="book.totalItems > 0" class="text-center text-2xl font-semibold text-gray-700 mb-8">
        {{ `${book.totalItems} Buku Ditemukan` }}
      </h2>
      <h2 v-else class="text-center text-2xl font-semibold text-gray-500 mb-8">Cari Data Buku</h2>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
        <BookCards v-for="{ volumeInfo, id } in book.items" :key="id">
          <template #header>
            <div class="relative group">
              <img
                :src="volumeInfo?.imageLinks?.thumbnail || 'https://via.placeholder.com/150'"
                :alt="volumeInfo?.title || 'No Title'"
                class="w-full h-64 object-cover transform transition-all duration-300 group-hover:scale-105"
              />
              <div
                class="absolute inset-0 bg-gradient-to-t from-black via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"
              ></div>
              <div
                class="absolute bottom-0 left-0 right-0 p-4 bg-gradient-to-t from-black to-transparent text-white"
              >
                <p class="font-bold text-lg">{{ volumeInfo?.title || 'No Title' }}</p>
                <p v-if="volumeInfo?.authors" class="text-sm mt-1">
                  {{ volumeInfo?.authors?.join(', ') || 'No Author' }}
                </p>
              </div>
            </div>
          </template>
          <template #content>
            <h3 class="font-semibold text-xl text-gray-800 mb-2">
              {{ volumeInfo?.title || 'No Title' }}
            </h3>
            <p class="text-gray-600 text-sm line-clamp-3 mb-4">
              {{ volumeInfo?.description || 'Deskripsi tidak tersedia' }}
            </p>
            <button
              class="w-full px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors duration-300"
            >
              Lihat Detail
            </button>
          </template>
        </BookCards>
      </div>
    </section>
  </div>
</template>

<style scoped>
.container {
  max-width: 1400px;
}
</style>
