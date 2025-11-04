<script setup lang="ts">
const answer1: string =
  "Lorem ipsum dolor sit amet consectetur adipisicing elit. Autem nihil ex dolor? Dolore impedit, ea iusto dolores temporibus quidem pariaturcupiditate eveniet molestiae non maxime nulla? Quo laboriosam doloremsint?";
const answer2: string =
  "Lorem ipsum dolor sit amet consectetur adipisicing elit. Autem nihil ex dolor? Dolore impedit, ea iusto dolores temporibus quidem pariaturcupiditate eveniet molestiae non maxime nulla? Quo laboriosam doloremsint?";
const answer3: string =
  "Lorem ipsum dolor sit amet consectetur adipisicing elit. Autem nihil ex dolor? Dolore impedit, ea iusto dolores temporibus quidem pariaturcupiditate eveniet molestiae non maxime nulla? Quo laboriosam doloremsint?";
const answer4: string =
  "Lorem ipsum dolor sit amet consectetur adipisicing elit. Autem nihil ex dolor? Dolore impedit, ea iusto dolores temporibus quidem pariaturcupiditate eveniet molestiae non maxime nulla? Quo laboriosam doloremsint?";
const answers = ref<string[]>([answer1, answer2, answer3, answer4]);
</script>

<template>
  <div class="bg"></div>
  <section class="questions">
    <div class="container content-box">
      <div class="question">
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
      </div>
      <div class="response">
        <h2>Content</h2>
        <p class="response__content">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Autem nihil
          ex dolor? Dolore impedit, ea iusto dolores temporibus quidem pariatur
          cupiditate eveniet molestiae non maxime nulla? Quo laboriosam dolorem
          sint?
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
h2 {
  justify-self: center;
  color: var(--text-dark);
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
  justify-items: left;
  counter-reset: q;
}

li {
  counter-increment: q;
  position: relative;
  width: min(34rem, 100%);
  color: var(--text-dark);
  background:
    linear-gradient(to right, #ddd, #fff, #ddd) padding-box,
    conic-gradient(
        from var(--angle),
        var(--brand) 0deg,
        color-mix(in oklab, var(--brand) 85%, var(--accent-amber) 15%) 160deg,
        color-mix(in oklab, var(--brand) 40%, var(--accent-amber) 60%) 190deg,
        var(--accent-amber) 210deg,
        color-mix(in oklab, var(--brand) 40%, var(--accent-amber) 60%) 230deg,
        color-mix(in oklab, var(--brand) 85%, var(--accent-amber) 15%) 300deg,
        var(--brand) 360deg
      )
      border-box;
  border: 5px solid transparent;
  border-radius: 100vw;
  box-shadow: 0 6px 24px -18px rgba(0, 0, 0, 0.6);
  font-size: 1.7rem;
  transition: transform 0.18s ease;
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
  transform: translateY(-2px);
}

li a {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  border-radius: inherit;
  position: relative;
  cursor: pointer;
  letter-spacing: 1px;
  padding: 0.9rem 3.5rem 0.9rem 3.5rem;
}

.question,
.response {
  padding: 2rem;
  border-radius: 1rem;
  box-shadow:
    rgba(0, 0, 0, 0.16) 0px 10px 36px 0px,
    rgba(0, 0, 0, 0.06) 0px 0px 0px 1px;
  background-color: var(--bg-light);
}

.questions {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
  text-align: center;
  height: 100vh;
}

.content-box {
  display: flex;
  justify-content: space-between;
}

.response {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.response__content {
  display: flex;
  color: var(--text-dark);
  font-size: 1.5em;
  max-width: 34rem;
  width: 100%;
  justify-content: flex-end;
  line-height: 1.2;
}

.bg {
  position: fixed;
  inset: 0;
  z-index: -1;
  pointer-events: none;
  background-image: linear-gradient(var(--brand));
}
</style>
