<script setup lang="ts"></script>

<template>
  <div class="body">
    <div class="container">
      <div class="content">
        <div class="left">
          <div class="video-left">
            <h2>Introduction to the Principle</h2>
            <iframe
              width="560"
              height="315"
              src="https://www.youtube.com/embed/YrpWBgB6oz8?si=8a0FJhNl_gOrL1lV"
              title="YouTube video player"
              frameborder="0"
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
              referrerpolicy="strict-origin-when-cross-origin"
              allowfullscreen
            ></iframe>
          </div>
          <div class="button-left">
            <button>Try it!</button>
          </div>
        </div>
        <div class="right">
          <div class="video-right">
            <h2>The Principle in Action</h2>
            <iframe
              width="560"
              height="315"
              src="https://www.youtube.com/embed/0vfU4cmdx-s?si=cL8JqJkhRjvoig1u"
              title="YouTube video player"
              frameborder="0"
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
              referrerpolicy="strict-origin-when-cross-origin"
              allowfullscreen
            ></iframe>
          </div>
          <div class="button-right">
            <button>Resources to Fight Manipulation</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
iframe {
  box-shadow: 0 rgba(0, 0, 0, 0.6);
  border-radius: 0.5rem;
  border: 4px solid var(--bg-paper);
}

h2 {
  color: #fff;
  font-size: 2rem;
  letter-spacing: 1px;
  line-height: 1.4;
  text-shadow: 1px 1px rgba(0, 0, 0, 0.3);
}

.body {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.content {
  display: flex;
  justify-content: space-between;
}

.left,
.right {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.button-left,
.button-right {
  width: 100%;
  display: flex;
  justify-content: center;
}

button {
  width: 80%;
  padding: 1rem;
  border-radius: 100vw;
  margin: 1rem 0;
  cursor: pointer;
  background:
    linear-gradient(to right, #ddd, #fff, #ddd) padding-box,
    linear-gradient(var(--bg-paper)) border-box;
  border: 5px solid transparent;
  border-radius: 100vw;
  box-shadow: 0 6px 24px -18px rgba(0, 0, 0, 0.6);
  font-size: 1.7rem;
  transition: transform 0.18s ease;
  animation: rotate 3s linear infinite;
  animation-play-state: paused;
}

button:hover,
button:focus-visible {
  animation-play-state: running;
  transform: translateY(-2px);
}
</style>
