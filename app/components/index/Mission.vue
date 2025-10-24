<script setup lang="ts"></script>

<template>
  <section class="questions">
    <h2>
      You can <em>recognize</em> and <span>Destroy</span><br />
      Manipulation by Asking:
    </h2>
    <ul>
      <li><a href="#">What's the MESSAGE?</a></li>
      <li><a href="">What's the METHOD?</a></li>
      <li><a href="">What's the MOTIVE?</a></li>
      <li><a href="">What's the COST?</a></li>
    </ul>
  </section>
</template>

<style scoped>
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

h2 {
  justify-self: center;
  color: var(--text);
  font-size: clamp(2rem, 2.5vw, 2.6rem);
  line-height: 1.15;
  letter-spacing: 1px;
  text-align: left;
}
ul {
  color: var(--text-dark);
  max-width: 42rem;
  margin: 1.25rem auto 0;
  padding: 0;
  display: grid;
  gap: 0.75rem;
  max-width: 42rem;
  justify-items: center;
  counter-reset: q;
}

li {
  counter-increment: q;
  position: relative;
  width: min(42rem, 100%);
  text-align: left;
  color: var(--text-dark);
  background:
    linear-gradient(var(--bg-paper) 0 0) padding-box,
    conic-gradient(
        from var(--angle),
        var(--accent),
        var(--secondary),
        var(--accent)
      )
      border-box;
  border: 4px solid transparent;
  border-radius: 100vw;
  box-shadow: 0 6px 24px -18px rgba(0, 0, 0, 0.6);
  font-size: 1.7rem;
  transition:
    transform 0.18s ease,
    box-shadow 0.18s ease,
    border-color 0.18s ease,
    margin 0.18s ease;
  display: flex;
  align-items: stretch;
  animation: rotate 3s linear infinite;
  animation-play-state: paused;
}

li::before {
  content: counter(q, decimal);
  position: absolute;
  left: 0.75rem;
  top: 50%;
  transform: translateY(-50%);
  width: 2.25rem;
  height: 2.25rem;
  border-radius: 100vw;
  display: grid;
  place-items: center;
  color: var(--text-dark);
  font-weight: 700;
}

li:hover,
li:focus-visible {
  animation-play-state: running;
}

li a {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  width: 100%;
  border-radius: inherit;
  position: relative;
  cursor: pointer;
  letter-spacing: 1px;
  padding: 0.9rem 1.25rem 0.9rem 3.5rem;
}

.questions {
  max-width: 70em;
  margin: 2rem auto;
  padding: 1rem;
  text-align: center;
}
</style>
