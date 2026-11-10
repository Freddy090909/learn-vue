<script setup lang="ts">
import { ref } from 'vue'
import vueLogo from '@/assets/logo_vue_300px.png'

const facts = ref([
  {
    title: "I'm lightweight",
    description:
      "I am incredibly small and fast! My core library is only around 30KB, so I won't slow you down.",
  },
  {
    title: "I'm approachable",
    description:
      'Easy to learn and use, even for beginners. I have a gentle learning curve, clear documentation, and a supportive community.',
  },
  {
    title: "I'm versatile",
    description:
      "I can handle everything from simple interactive elements to complex single-page applications. I'm great for small projects and large-scale applications alike.",
  },
])
</script>

<template>
  <div class="vue-facts-view">
    <div class="container">
      <header>
        <img class="vue-logo" :src="vueLogo" alt="Vue logo" width="150" height="150" />
        <h1>Vue facts</h1>
      </header>
      <main>
        <section v-for="fact in facts" :key="fact.title">
          <h2>{{ fact.title }}</h2>
          <p>{{ fact.description }}</p>
        </section>
      </main>
      <footer>
        <p>Learn more about me at <a target="_blank" href="https://vuejs.org/">vuejs.org</a></p>
      </footer>
    </div>
  </div>
</template>

<style scoped>
.vue-logo {
  display: block;
  max-width: 100%;
  height: auto;
  margin: 0 auto;
}

.vue-facts-view {
  background-color: #42b883;
  display: flex;
  justify-content: center;
  padding: 1rem;
}

.container {
  padding: 1rem 1.5rem;
  background: #fff;
  border: 1px solid #ddd;
  border-radius: 0.5rem;
  display: inline-flex;
  flex-direction: column;
  max-width: 50ch;
}
</style>
