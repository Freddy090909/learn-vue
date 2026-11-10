<script setup lang="ts">
import { ref } from 'vue'

const name = ref('World')
const emoji = ref('🦃')
const currentYear = ref(new Date().getFullYear())
</script>

<template>
  <header>
    <div class="emoji">{{ emoji }}</div>
  </header>
  <main>
    <h1>Hello {{ name }}</h1>
  </main>
  <footer>
    <div>&copy; {{ currentYear }}</div>
  </footer>
</template>

<style scoped>
header,
main,
footer {
  display: flex;
  flex-direction: column;
  align-items: center;
}

header > .emoji {
  font-size: 64px;
}
</style>
