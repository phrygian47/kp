<script setup lang="ts">
import type { AccordionItem } from "@nuxt/ui";
import Accordion from "../Accordion.vue";
const items = ref<AccordionItem[]>([
  {
    label: "What's The MESSAGE?",
    content:
      "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris quis elit vel risus vestibulum eleifend sit amet nec ipsum. Etiam hendrerit est in mi tempus elementum. Mauris venenatis arcu velit. Ut a eros in neque eleifend placerat. Donec neque odio, bibendum id justo in, tempor tincidunt lorem. Nullam in sapien vitae elit pharetra placerat id non sapien. Donec ac dapibus purus. Etiam placerat rutrum tincidunt. Aenean sagittis iaculis ornare. Aliquam euismod, risus a tempus fermentum, mi dui tempor lacus, at porta ligula lacus faucibus elit. Suspendisse potenti. Ut porta tortor non ex aliquam viverra.",
  },
  {
    label: "What's the METHOD?",
    content:
      "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris quis elit vel risus vestibulum eleifend sit amet nec ipsum. Etiam hendrerit est in mi tempus elementum. Mauris venenatis arcu velit. Ut a eros in neque eleifend placerat. Donec neque odio, bibendum id justo in, tempor tincidunt lorem. Nullam in sapien vitae elit pharetra placerat id non sapien. Donec ac dapibus purus. Etiam placerat rutrum tincidunt. Aenean sagittis iaculis ornare. Aliquam euismod, risus a tempus fermentum, mi dui tempor lacus, at porta ligula lacus faucibus elit. Suspendisse potenti. Ut porta tortor non ex aliquam viverra.",
  },
  {
    label: "What's the MOTIVE?",
    content:
      "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris quis elit vel risus vestibulum eleifend sit amet nec ipsum. Etiam hendrerit est in mi tempus elementum. Mauris venenatis arcu velit. Ut a eros in neque eleifend placerat. Donec neque odio, bibendum id justo in, tempor tincidunt lorem. Nullam in sapien vitae elit pharetra placerat id non sapien. Donec ac dapibus purus. Etiam placerat rutrum tincidunt. Aenean sagittis iaculis ornare. Aliquam euismod, risus a tempus fermentum, mi dui tempor lacus, at porta ligula lacus faucibus elit. Suspendisse potenti. Ut porta tortor non ex aliquam viverra.",
  },
  {
    label: "What's the COST?",
    content:
      "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris quis elit vel risus vestibulum eleifend sit amet nec ipsum. Etiam hendrerit est in mi tempus elementum. Mauris venenatis arcu velit. Ut a eros in neque eleifend placerat. Donec neque odio, bibendum id justo in, tempor tincidunt lorem. Nullam in sapien vitae elit pharetra placerat id non sapien. Donec ac dapibus purus. Etiam placerat rutrum tincidunt. Aenean sagittis iaculis ornare. Aliquam euismod, risus a tempus fermentum, mi dui tempor lacus, at porta ligula lacus faucibus elit. Suspendisse potenti. Ut porta tortor non ex aliquam viverra.",
  },
]);
</script>

<template>
  <section class="questions">
    <div class="container content-box">
      <div class="question">
        <h2>
          You can Recognize and <span>Destroy</span>
          Manipulation by Asking
        </h2>
      </div>
      <div class="response">
        <div class="response__content">
          <Accordion
            :items="items"
            type="single"
            :collapsible="true"
            :unmount-on-hide="false"
            text="#f8fafc"
            select="#e6a900"
          ></Accordion>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
h2 {
  justify-self: center;
  color: var(--text-dark);
  font-size: clamp(4.5rem, 4.7vw, 5rem);
  line-height: 1.15;
  letter-spacing: 1px;
  text-align: left;
}

.question,
.response {
  padding: 2rem;
  width: 100%;
  height: 100%;
}

.question {
  overflow-y: auto;
  border-radius: 0;
  background-color: var(--bg-light);
  box-shadow:
    rgba(0, 0, 0, 0.16) 0px 10px 36px 0px,
    rgba(0, 0, 0, 0.06) 0px 0px 0px 1px;
  scrollbar-gutter: stable;
}

.questions {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
  text-align: center;
  height: 100vh;
  width: 100%;
}

.content-box {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
  max-height: 70%;
  height: 100%;
}

.response__content {
  color: var(--text-dark);
  font-size: 1.5em;
  width: 100%;
  height: 100%;
}
</style>
