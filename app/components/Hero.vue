<script setup lang="ts">
import { onMounted } from "vue";
import bg from "~/assets/background.png";
import bg_color from "~/assets/background-colorized.png";

const smoothScroll = (sel: string) => {
  const el = document.querySelector(sel);
  if (el) el.scrollIntoView({ behavior: "smooth", block: "start" });
};

const onChipClick = () => {
  console.log("Button Pressed!");
};

onMounted(() => {
  document.querySelector(".hero .content")?.classList.add("is-visible");
});
</script>

<template>
  <section
    class="hero"
    :style="{
      '--hero-image': `url(${bg})`,
      '--hero-image-2': `url(${bg_color})`,
      '--hero-y': '35%',
    }"
    aria-labelledby="hero-title"
  >
    <div class="hero__bg"></div>
    <div class="hero__bg hero__bg--2"></div>
    <div class="overlay"></div>
    <div class="content">
      <div class="grid-item">
        <h1 id="hero-title" class="h1">The <br />Keokuk <br />Principle</h1>
      </div>
      <div></div>
      <div class="grid-item right">
        <h2 class="sub">
          Gain <br />
          the Clarity <br />You're Missing
        </h2>
        <NuxtLink to="/book" class="btn btn--secondary">Get the Book</NuxtLink>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  min-height: 70vh;
  display: grid;
  place-items: center;
  overflow: hidden;
}

.content {
  width: 100%;
  opacity: 0;
  transform: translateY(10px);
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  transition:
    opacity 0.5s ease,
    transform 0.5s ease;
}

.content.is-visible {
  opacity: 1;
  transform: none;
}

.hero__bg {
  position: absolute;
  inset: 0;
  z-index: -2;
  background-image: var(--hero-image);
  background-size: cover;
  background-position: center var(--hero-y, 50%);
  filter: grayscale(1) contrast(1.1) brightness(1);
  transform: scale(1.08);
  animation: kb 26s ease-in-out infinite alternate;
}

.hero__bg--2 {
  position: absolute;
  inset: 0;
  z-index: -2;
  background-image: var(--hero-image-2);
  background-size: cover;
  background-position: center var(--hero-y, 50%);
  animation: kb 26s ease-in-out infinite alternate;
  mask-image: linear-gradient(to right, transparent 40%, black 100%);
  mask-size: 100% 100%;
  opacity: 0.9;
  filter: contrast(2) brightness(2.5);
}

@keyframes kb {
  to {
    transform: scale(1.2) translateY(-1.5%);
  }
}
.overlay {
  position: absolute;
  inset: 0;
  z-index: -1;
  background:
    linear-gradient(
      to top,
      rgba(15, 23, 42, 0.9) 0%,
      rgba(15, 23, 42, 0.45) 35%,
      rgba(15, 23, 42, 0.15) 70%,
      rgba(248, 250, 252, 1) 100%
    ),
    radial-gradient(
      1000px 500px at 85% 10%,
      rgba(37, 99, 235, 0.28),
      transparent 60%
    );
  mix-blend-mode: multiply;
}

.h1 {
  font-family: "Source Serif 4", Georgia, serif;
  font-weight: 800;
  line-height: 1.05;
  font-size: clamp(40px, 7vw, 64px);
  color: #fff;
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

.grid-item {
  display: block;
  place-self: center;
  margin: 0 auto;
}

.grid-item.right {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: center;
  gap: 1rem;
}

.btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.8rem 1.1rem;
  border-radius: 100vw;
  font-weight: 700;
  border: 1px solid transparent;
  text-decoration: none;
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
