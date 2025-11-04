<script setup lang="ts">
import type { DefineComponent } from "vue";

const HeroPanel = defineAsyncComponent(
  () => import("~/components/index/Hero.vue")
);
const MissionPanel = defineAsyncComponent(
  () => import("~/components/index/Mission.vue")
);
const VideoPanel = defineAsyncComponent(
  () => import("~/components/index/Videos.vue")
);

type PanelId = 1 | 2 | 3;

type PanelLabel = "Hero" | "Mission" | "Videos";

type Dir = "up" | "down" | null;

type Panel = {
  id: PanelId;
  label: PanelLabel;
  component: DefineComponent<any, any, any>;
};

const direction = ref<Dir>(null);

const panels = ref<Panel[]>([
  { id: 1, label: "Hero", component: HeroPanel },
  { id: 2, label: "Mission", component: MissionPanel },
  { id: 3, label: "Videos", component: VideoPanel },
]);

const current = ref<number>(1);

const activeComponent = computed(
  () => panels.value.find((p) => p.id === current.value)!
);
</script>

<template>
  <div class="bg"></div>
  <div class="pagination">
    <Suspense>
      <template #default>
        <KeepAlive>
          <div
            :id="`panel-${activeComponent.id}`"
            role="tabpanel"
            :aria-labelledby="`tab-${activeComponent.id}`"
          >
            <component
              :is="activeComponent.component"
              :key="activeComponent.id"
            />
          </div>
        </KeepAlive>
      </template>
      <template #fallback>
        <div class="p-6 text-sm opacity-70">Loading…</div>
      </template>
    </Suspense>
    <nav class="nav-dots" role="tablist" aria-label="Panels">
      <button
        v-for="p in panels"
        :key="p.id"
        role="tabs"
        @click="current = p.id"
        :aria-controls="`panel-${p.id}`"
        :aria-selected="p.id === current"
        :class="['dot', { 'dot-active': p.id === current }]"
        class="dot"
      >
        <Icon name="icon-park-outline:dot" aria-hidden="true" />
      </button>
    </nav>
  </div>
</template>

<style lang="css" scoped>
.nav-dots {
  display: flex;
  position: absolute;
  bottom: 0;
  justify-content: center;
  width: 100%;
  padding: 1.5rem;
}

.bg {
  position: fixed;
  inset: 0;
  z-index: -1;
  pointer-events: none;
  background-image: linear-gradient(var(--brand));
}

.dot {
  background: transparent;
  color: #fff;
  opacity: 0.6;
  transition:
    opacity 0.2s ease,
    transform 0.2s ease;
}

.dot-active {
  opacity: 1;
  transform: scale(1.2);
}

button {
  background: transparent;
  border: transparent;
  cursor: pointer;
}
</style>
