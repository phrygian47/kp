<script setup lang="ts">
import Accordion from "~/components/faq/Accordion.vue";
</script>

<template>
  <div class="container center">
    <div class="banner"><h2>Frequently Asked Questions</h2></div>
    <div class="faq">
      <div class="faq__header"><h3>FAQs</h3></div>
      <div class="faq__content">
        <Accordion></Accordion>
      </div>
    </div>
  </div>
</template>

<style scoped>
h2 {
  font-size: 5rem;
  color: var(--text);
}

h3 {
  font-size: 3rem;
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
  display: flex;
  justify-content: center;
}

.faq {
  width: 50%;
}

.faq__content {
  padding: 1rem 0;
}
</style>
