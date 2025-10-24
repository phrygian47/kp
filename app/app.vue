<script setup lang="ts">
import Header from "./components/Header.vue";
</script>

<template>
  <div class="background"></div>
  <header>
    <Header></Header>
  </header>
  <NuxtPage />
</template>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

:root {
  --background-color: #eae3d7;
  --background-main: #0e0f11;
  --bg-ink: #0b0f14;
  --bg-slate: #1f2937;
  --bg-paper: #f5f1e8;
  --text: #f8fafc;
  --text-dark: #0f172a;
  --muted: #94a3b8;

  --primary: #0f766e;
  --primary-hover: #115e59;
  --primary-bright: #2dd4bf;
  --secondary: #b45309;
  --accent: #eab308;
}

li {
  list-style: none;
}

a {
  display: block;
  text-decoration: none;
  color: #fff;
}

a:visited {
  color: inherit;
}

a:hover::after {
  transform: scaleX(1);
}

.background {
  position: fixed;
  inset: 0;
  background: var(--background-main);
  z-index: -50;
}

.container {
  width: 100%;
  margin-left: auto;
  margin-right: auto;
  padding-left: 1rem;
  padding-right: 1rem;
}

@media (min-width: 640px) {
  .container {
    max-width: 640px;
  }
}

@media (min-width: 768px) {
  .container {
    max-width: 768px;
  }
}

@media (min-width: 1024px) {
  .container {
    max-width: 1024px;
  }
}

@media (min-width: 1280px) {
  .container {
    max-width: 1280px;
  }
}

@media (min-width: 1536px) {
  .container {
    max-width: 1536px;
  }
}
</style>
