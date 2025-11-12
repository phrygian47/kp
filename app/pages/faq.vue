<script setup lang="ts"></script>

<template>
  <div class="container center">
    <div class="banner"><h2>Frequently Asked Questions</h2></div>
    <div class="faq">
      <div class="faq__header"><h3>FAQs</h3></div>
      <div class="faq__content">Content here</div>
    </div>
  </div>
</template>

<style scoped>
h2 {
  font-size: 4rem;
  color: var(--text);
}

h3 {
  font-size: 2rem;
  color: var(--text);
}

.center {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.banner {
  width: 50%;
  margin: 4rem;
  border: 1px solid red;
  display: flex;
  justify-content: center;
}

.faq {
  width: 50%;
}

.faq__header {
  border: 1px solid red;
}

.faq__content {
  border: 1px solid red;
}
</style>
