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

@property --angle {
  syntax: "<angle>";
  initial-value: 0deg;
  inherits: true;
}
@keyframes rotate {
  to {
    --angle: 1turn;
  }
}

:root {
  --bg-light: #eae3d7;
  --background-main: #0e0f11;
  --bg-ink: #0b0f14;
  --bg-slate: #1f2937;
  --bg-paper: #667d6f;
  --brand: #667d6f;
  --bg-alt: #00b300;
  --text: #f8fafc;
  --text-dark: #2a2e2b;
  --muted: #94a3b8;

  --primary: #003f88;
  --primary-hover: #00296b;
  --primary-bright: #007fc9;
  --secondary: #553c74;
  --accent: #743c5b;
  --accent-amber: #e6a900;

  --conic-grad: conic-gradient(
    from var(--angle),
    color-mix(in oklab, var(--brand) 92%, white) 0% 10%,
    var(--brand) 10% 28%,
    color-mix(in oklab, var(--brand) 70%, black) 28% 34%,
    var(--brand) 34% 60%,
    color-mix(in oklab, var(--brand) 65%, black) 60% 66%,
    var(--brand) 66% 88%,
    color-mix(in oklab, var(--brand) 90%, white) 88% 100%
  );
}

html {
  scrollbar-gutter: stable;
  overflow-y: scroll;
  scroll-behavior: smooth;
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
  background: linear-gradient(var(--brand));
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
