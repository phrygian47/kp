<script setup lang="ts">
import { onMounted } from "vue";
import keokukPortrait from "~/assets/keokuk-portrait.png";

const show = ref(false);

const smoothScroll = (sel: string) => {
  const el = document.querySelector(sel);
  if (el) el.scrollIntoView({ behavior: "smooth", block: "start" });
};

const onChipClick = () => {
  console.log("Button Pressed!");
};

onMounted(() => {
  show.value = true;
});
</script>

<template>
  <section class="intro-page" aria-labelledby="intro-page">
    <div class="content container" :class="{ 'is-visible': show }">
      <div class="intro-text">
        <div class="intro-text__content">
          <h1 id="hero-title" class="h1">The <br />Keokuk <br />Principle</h1>
          <div class="btns">
            <NuxtLink to="/book" class="btn btn--secondary"
              >Find Out More</NuxtLink
            >
            <NuxtLink to="/book" class="btn btn--secondary"
              >Get the Book</NuxtLink
            >
          </div>
        </div>
      </div>
      <div class="intro-img">
        <img
          :src="keokukPortrait"
          alt="Portrait of Keokuk Chief Sauk"
          height="700"
          width="550"
        />
      </div>
    </div>
  </section>
</template>

<style scoped>
.btns {
  display: flex;
  gap: 2rem;
  margin: 1.7rem 0;
}

.content {
  display: flex;
  justify-content: space-between;
  width: 100%;
  padding: 1rem;
  opacity: 0;
  transform: translateY(10px);
  transition:
    opacity 0.5s ease,
    transform 0.5s ease;
}

.content.is-visible {
  opacity: 1;
  transform: none;
}

.h1 {
  font-family: "Source Serif 4", Georgia, serif;
  font-weight: 800;
  line-height: 1.05;
  font-size: clamp(40px, 7vw, 64px);
  color: #fff;
}

.intro-page {
  display: flex;
  align-items: center;
  height: 100vh;
}

.intro-img,
.intro-text {
  margin-left: 4rem;
  margin-right: 4rem;
}

.intro-img {
  position: relative;
  padding: 1rem;
  border: 0;
  box-shadow: none;
  outline: none;
  user-select: none;
}

.intro-img::after {
  content: "";
  position: absolute;
  inset: 0;
  background: radial-gradient(
    transparent 0%,
    rgba(0, 0, 0, 0.3) 45%,
    var(--brand) 56%
  ); 
  z-index: 10;
  border-radius: 100vh;
  transform: scale(1.2);
}

.intro-text {
  width: 100%;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}

img {
  border-radius: 100vh;
}

.sub {
  color: #e5e7eb;
  font-family: "Source Serif 4", Georgia, serif;
  font-size: clamp(34px, 7vw, 56px);
  font-weight: 800;
  line-height: 1.05;
  max-width: 760px;
  text-align: right;
}

.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 1rem 1.7rem;
  margin-top: 0.5rem;
  border-radius: 100vw;
  font-weight: 700;
  border: 1px solid transparent;
  text-decoration: none;
  font-size: 1.1rem;
  letter-spacing: 1px;
  transition: transform 0.18s ease;
}

.btn:hover,
.btn:focus-visible {
  transform: translateY(-4px);
}

.btn--primary {
  background: #2563eb;
  color: #fff;
}

.btn--secondary {
  background: rgba(248, 250, 252, 0.9);
  color: #0f172a;
  border-color: rgba(15, 23, 42, 0.08);
}
</style>
