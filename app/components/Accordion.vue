<script setup lang="ts">
import type { AccordionItem } from "@nuxt/ui";

const props = withDefaults(
  defineProps<{
    items: AccordionItem[];
    type?: "single" | "multiple";
    collapsible?: boolean;
    unmountOnHide?: boolean;
    text: string;
    select: string;
  }>(),
  {
    type: "single",
    collapsible: true,
    unmountOnHide: false,
  }
);

const accordionUi = {
  root: "acc",
  item: "acc-item",
  header: "acc-header",
  trigger: "acc-trigger",
  label: "acc-label",
  trailingIcon: "acc-hide",
  content: "acc-content",
  body: "acc-body",
};
</script>

<template>
  <div
    class="acc-wrapper"
    :style="{
      '--acc-label': text,
      '--acc-body': text,
      '--acc-label-active': select,
      '--acc-body-active': select,
    }"
  >
    <UAccordion
      :items="items"
      :ui="accordionUi"
      trailing-icon="none"
      :unmount-on-hide="false"
      :collapsible="true"
    >
      <template #body="{ item }">
        <slot name="body" :item="item">
          {{ item.content }}
        </slot>
      </template>
    </UAccordion>
  </div>
</template>

<style scoped>
:deep(.acc) {
  background: transparent;
}

:deep(.acc-item) {
  border-bottom: 1px solid #e5e7ee;
}

:deep(.acc-header) {
  display: block;
}

:deep(.acc-trigger) {
  position: relative;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 0.7rem 1.5rem 0.7rem 0;
  background: none;
  border: 0;
  text-align: left;
  cursor: pointer;
  color: var(--acc-label);
  font-size: 3rem;
}

:deep(.acc-label) {
  font-weight: 400;
  transition: color 0.24s ease;
}

:deep([data-state="open"] .acc-label) {
  color: var(--acc-label-active);
  font-weight: 600;
}

:deep(.acc-trigger::after),
:deep(.acc-trigger::before) {
  content: "";
  position: absolute;
  right: 4px;
  top: 50%;
  transform: translateY(-50%);
  background: var(--acc-label);
  border-radius: 1px;
  transition:
    transform 0.18s ease,
    opacity 0.18s ease,
    background-color 0.18s ease;
  margin-right: 0.75rem;
}

:deep(.acc-trigger::after) {
  width: 14px;
  height: 2px;
}

:deep(.acc-trigger::before) {
  width: 2px;
  height: 14px;
  right: 10px;
}

:deep([data-state="open"] .acc-trigger::after) {
  background: var(--acc-label-active);
}

:deep([data-state="open"] .acc-trigger::before) {
  transform: translateY(-50%) scaleY(0);
  opacity: 0;
  transition:
    transform 0.18s ease,
    opacity 0.18s ease;
}

:deep(.acc-content) {
  color: var(--text);
  text-align: justify;
  font-size: 1.2rem;
}

:deep(.acc-content[data-state="open"]) {
  animation: acc-slide-down 0.24s ease-out;
}

:deep(.acc-content[data-state="closed"]) {
  animation: acc-slide-up 0.24s ease-out;
}

:deep(.acc-body) {
  padding: 1rem;
  line-height: 1.55;
}

.scroll-wrapper {
  overflow-y: hidden;
  margin-bottom: 4rem;
}

@keyframes acc-slide-down {
  from {
    height: 0;
    opacity: 0;
  }
  to {
    height: var(--reka-accordion-content-height);
    opacity: 1;
  }
}

@keyframes acc-slide-up {
  from {
    height: var(--reka-accordion-content-height);
    opacity: 1;
  }
  to {
    height: 0;
    opacity: 0;
  }
}

@media (prefers-reduced-motion: reduce) {
  :deep(.acc-content),
  :deep(.acc-trigger::before),
  :deep(.acc-trigger::after) {
    transition: none;
  }
}
</style>
