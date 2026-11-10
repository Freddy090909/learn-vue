<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/hello-world">Hello World</RouterLink>
      <RouterLink to="/about">About</RouterLink>
    </nav>

    <div>Navigate somewhere</div>
  </header>

  <RouterView />
</template>

<style scoped></style>
