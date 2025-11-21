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

const SCROLL_DELAY = 500; //ms

const panels = ref<Panel[]>([
  { id: 1, label: "Hero", component: HeroPanel },
  { id: 2, label: "Mission", component: MissionPanel },
  { id: 3, label: "Videos", component: VideoPanel },
]);

const current = ref<number>(1);

const activeComponent = computed(
  () => panels.value.find((p) => p.id === current.value)!
);

function handleChildClick(nextId?: number) {
  //For learn more button on first page, default 2.
  current.value = (nextId as PanelId) ?? 2;
}

let wheelTimeout = false;

const onWheel = (event: WheelEvent) => {
  if (wheelTimeout) return;
  let changed = false;
  if (event.deltaY > 0) {
    if (current.value >= 3) {
      return;
    }
    current.value = (current.value + 1) as PanelId;
    changed = true;
  }
  if (event.deltaY < 0) {
    if (current.value <= 1) {
      return;
    }
    current.value = (current.value - 1) as PanelId;
    changed = true;
  }
  if (!changed) return;

  wheelTimeout = true;
  setTimeout(() => {
    wheelTimeout = false;
  }, SCROLL_DELAY);
};

onMounted(() => {
  window.addEventListener("wheel", onWheel, { passive: true });
});
onBeforeUnmount(() => {
  window.removeEventListener("wheel", onWheel);
});
</script>

<template>
  <div class="bg"></div>
  <div class="pagination">
    <Suspense>
      <template #default>
        <!-- KeepAlive is optional now; v-show keeps DOM in place -->
        <KeepAlive>
          <div
            v-for="p in panels"
            :key="p.id"
            :id="`panel-${p.id}`"
            role="tabpanel"
            :aria-labelledby="`tab-${p.id}`"
            v-show="p.id === current"
          >
            <component :is="p.component" @clicked="handleChildClick" />
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
        role="tab"
        @click="current = p.id"
        :aria-controls="`panel-${p.id}`"
        :aria-selected="p.id === current"
        :class="['dot', { 'dot-active': p.id === current }]"
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
