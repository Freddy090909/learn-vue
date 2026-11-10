<script setup lang="ts">
import { RouterLink } from 'vue-router'
</script>

<template>
  <header>
    <nav aria-label="Main navigation">
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/hello-world">Hello World</RouterLink>
      <RouterLink to="/quote-generator">Quote Generator</RouterLink>
      <RouterLink to="/about">About</RouterLink>
    </nav>
  </header>
</template>

<style scoped>
header {
  margin-bottom: 1.5rem;
  padding: 1rem 1.5rem;
  background: #fff;
  border: 1px solid #ddd;
  border-radius: 0.5rem;
}

nav {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

nav a {
  padding: 0.5rem 0.75rem;
  border-radius: 0.375rem;
  color: #334155;
  font-weight: 600;
  text-decoration: none;
}

nav a:hover {
  background: #f1f5f9;
}

nav a.router-link-exact-active {
  background: #e0e7ff;
  color: #3730a3;
}

nav a:focus-visible {
  outline: 2px solid #4f46e5;
  outline-offset: 2px;
}
</style>
