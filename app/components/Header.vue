<script setup lang="ts">
import type { NavigationMenuItem } from "@nuxt/ui";
import { useRoute } from "vue-router";
import { computed } from "vue";

const route = useRoute();

const isHome = computed(() => route.path === "/");

const items = computed<NavigationMenuItem[]>(() => [
  {
    label: "Home",
    to: "/",
  },
  {
    label: "About",
    to: "/about",
  },
  {
    label: "The Book",
    to: "/book",
  },
  {
    label: "Resources",
    to: "/resources",
  },
  {
    label: "FAQs",
    to: "/faq",
  },
  {
    label: "Donate",
    to: "/donate",
  },
  {
    label: "Contact",
    to: "/contact",
  },
]);
</script>

<template>
  <div :class="['outer-header', { 'outer-header--home': isHome }]">
    <div :class="['header', { 'header--alt': !isHome }]">
      <nav class="container" aria-label="Primary">
        <ul class="navbar">
          <li v-for="item in items" :key="item.label">
            <NuxtLink :to="item.to" class="link">{{ item.label }}</NuxtLink>
          </li>
        </ul>
      </nav>
    </div>
  </div>
</template>

<style scoped>
nav {
  display: flex;
  justify-content: center;
  padding: 8px;
  width: 100%;
}

.navbar {
  display: flex;
  justify-content: flex-end;
  gap: 4rem;
}

.outer-header--home {
  position: fixed;
  inset: 0;
  width: 100%;
  z-index: 10;
  pointer-events: none;
}

.header {
  padding: 1rem 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  min-height: 65px;
  max-height: 70px;
  pointer-events: all;
  background: rgba(0, 0, 0, 0);
}

.header--alt {
  background: none;
  background: #000;
}

.header .logo {
  font-size: 1.6rem;
  font-weight: 600;
  letter-spacing: 1px;
  font-family:
    "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande", "Lucida Sans",
    Arial, sans-serif;
  color: #fff;
}

.link::after {
  content: "";
  position: relative;
  display: block;
  width: 100%;
  height: 3px;
  border-radius: 2px;
  bottom: 0;
  left: 0;
  background-color: var(--accent-amber);
  transform: scaleX(0);
  transform-origin: bottom left;
  transition: transform 0.3s ease-out;
}

.link:hover::after {
  transform: scaleX(1);
}

li {
  display: flex;
  align-items: center;
  font-size: 1.3rem;
  letter-spacing: 2px;
  line-height: 1.2;
  font-weight: 600;
  font-family:
    "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande", "Lucida Sans",
    Arial, sans-serif;
  color: #fff;
}
</style>
