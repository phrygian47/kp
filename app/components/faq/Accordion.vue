<script setup lang="ts">
import type { AccordionItem } from "@nuxt/ui";
const items = ref<AccordionItem[]>([
  {
    label: "Who is Keokuk?",
    content:
      "Keokuk was a Sauk Indian chief who lived at a time of great racial tensions, namely between the “whites” and the Natives. Another chief, Blackhawk, came with 300 warriors to Keokuk's village in April 1832 with the intent of enlisting Keokuk and his warriors to join him in crossing the Mississippi and attacking the whites and taking back their ancestral homelands. After Blackhawk's powerful, manipulative speech had whipped the warriors into a frenzy, Keokuk's speech brilliantly countered Blackhawk's manipulations and gave birth to the Keokuk Principle that we can use today to do the same.",
  },
  {
    label: "How am I defining manipulation?",
    content:
      "Manipulation is approaching someone (the Message) using a Method between reasoning and force to get what you want (the Motive) without regard to the Cost to others or even yourself.",
  },
  {
    label: "Is manipulation always bad?",
    content:
      "No. Deceit is often used to successfully pull off a surprise birthday party, for example. And there is the example from the movie “Young Frankenstein” where the doctor is having his assistants lock him in a room with the monster who is probably ready to tear him apart, but the doctor uses flattery to gain control of the monster and to save his own life. During World War Two, to minimize the loss of Allied lives when storming the beaches of Normandy, the Allies put false documents on a body in the water to indicate that the D-Day Invasion was going to happen at a different place. That intelligence operation worked out well for the Allies, at least. It is important to look at the Motive in addition to the Method, and it is always important to look at the Cost. In these examples, the Cost of using the manipulative Method was not negative (except for the Axis powers).",
  },
  {
    label: "Am I Native American?",
    content: "No.",
  },
  {
    label:
      "Does my use of these Native American speeches constitute cultural appropriation?",
    content:
      "I am looking for truth everywhere, among all cultures, and will gladly incorporate any truths I find into my life. I do so with total respect and with full acknowledgement of where that particular truth came from. I believe that God gives light and truth to all people everywhere in proportion to their willingness to live according to such light and truth, and that wisdom can be found worldwide and throughout time. In the words of Tatanga Mani, “My people have been searching for truth for generations, and they continue to find it. All races of people have conducted such searches. Perhaps that explains why nearly all the world's religions have points in common, like charity, forgiveness, and belief in a life after death.” When you look up dictionary definitions for “cultural appropriation” there are elements of disrespect, failure to acknowledge the source, using things out of context, etc. That is simply not the case with what I am doing. (MacEwan, Grant. 1969. Tatanga Mani: Walking Buffalo of the Stonies. Edmonton, Hurtig Publishers, 181-82.)",
  },
]);
</script>

<template>
  <div class="scroll-wrapper">
    <UAccordion
      trailing-icon="none"
      type="single"
      :ui="{
        root: 'acc',
        item: 'acc-item',
        header: 'acc-header',
        trigger: 'acc-trigger',
        label: 'acc-label',
        trailingIcon: 'acc-hide',
        content: 'acc-content',
        body: 'acc-body',
      }"
      :unmount-on-hide="false"
      :items="items"
    >
      <template #body="{ item }">
        {{ item.content }}
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
  color: var(--text);
  font-size: 1.5rem;
  text-transform: uppercase;
}
:deep(.acc-label) {
  font-weight: 400;
  transition: color 0.24s ease;
}

:deep([data-state="open"] .acc-label) {
  color: var(--accent-amber);
  font-weight: 600;
}

:deep(.acc-trigger::after),
:deep(.acc-trigger::before) {
  content: "";
  position: absolute;
  right: 4px;
  top: 50%;
  transform: translateY(-50%);
  background: var(--text);
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
  background: var(--accent-amber);
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
