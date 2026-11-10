<script setup lang="ts">
import { onMounted, ref } from 'vue'

const quote = ref({
  quote: 'First, solve the problem. Then, write the code.',
  author: 'John Johnson',
})
const isLoading = ref(false)
const error = ref('')

async function generateQuote() {
  if (isLoading.value) return

  isLoading.value = true
  error.value = ''

  try {
    const response = await fetch('https://dummyjson.com/quotes/random', { cache: 'no-store' })
    if (!response.ok) throw new Error('Failed to fetch quote')

    const data = await response.json()
    if (typeof data.quote !== 'string' || typeof data.author !== 'string') {
      throw new Error('Invalid quote response')
    }
    quote.value = { quote: data.quote, author: data.author }
  } catch {
    error.value = 'Could not load a quote. Please try again.'
  } finally {
    isLoading.value = false
  }
}

onMounted(generateQuote)
</script>

<template>
  <div class="quote-generator-view">
    <header>
      <h1>Quote generator</h1>
    </header>
    <main class="quote-container">
      <div aria-live="polite" :aria-busy="isLoading">
        <div class="quote">"{{ quote.quote }}"</div>
        <div class="quoted-person">{{ quote.author }}</div>
      </div>
      <p v-if="error" role="alert">{{ error }}</p>
      <button class="generate-quote" :disabled="isLoading" @click="generateQuote">
        {{ isLoading ? 'Loading...' : 'Another!' }}
      </button>
    </main>
    <footer>
      <div>Created by <span class="signature">Fred</span> &copy; 2026</div>
    </footer>
  </div>
</template>

<style scoped>
.quote-generator-view {
  background-color: #4f46e5;
  padding: 0.5rem;
  border-radius: 0.25rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #e0e7ff;
}

.quote-container {
  color: black;
  background-color: #8899ff;
  border: 1px solid #3730a3;
  border-top-right-radius: 0.25rem;
  border-bottom-left-radius: 0.25rem;
  padding: 0.5rem;
}

.quote {
  font-size: 2rem;
  font-style: italic;
  text-wrap: pretty;
  max-width: 25ch;
}

.quoted-person {
  color: #334155;
  text-align: right;
  margin-bottom: 2rem;
}

.generate-quote {
  display: block;
  margin: 0 auto;
}

.quoted-person::before {
  content: '- ';
}

footer {
  margin-top: 1rem;
}

.signature {
  font-family: 'Great Vibes', cursive;
}
</style>
