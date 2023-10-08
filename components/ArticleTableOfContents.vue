<script lang="ts" setup>
import { TocLink } from "@nuxt/content/dist/runtime/types";

// toc variable that contains the <h2> and <h3> tags from our article
const props = defineProps<{
  toc: TocLink[];
}>();

const activeToc = ref<string | null>(null);

function isScrollAtEndOfWindow(): boolean {
  return (
    window.innerHeight + Math.round(window.scrollY) >=
    document.body.offsetHeight - 150
  );
}

function onScrollGetActiveToc() {
  const scrollY = window.scrollY;

  // take last toc if scrolled to end of window
  if (isScrollAtEndOfWindow()) {
    activeToc.value = [...props.toc].pop()?.id ?? null;
    return;
  }

  // retrieve the active state of toc
  for (const link of [...props.toc].reverse()) {
    const el = document.getElementById(link.id);
    if (!el) {
      continue;
    }

    if (scrollY >= el.offsetTop - 150) {
      activeToc.value = link.id;
      return;
    }
  }
}

onMounted(() => {
  window.addEventListener("scroll", onScrollGetActiveToc);
});
onUnmounted(() => {
  window.removeEventListener("scroll", onScrollGetActiveToc);
});
</script>
<template>
  <aside>
    <div class="mb-2 font-semibold">Table of Contents</div>
    <ul class="not-prose m-0 flex list-none flex-col gap-4 p-0">
      <li v-for="{ id, text } in toc" :key="id" class="m-0 p-0 leading-tight">
        <NuxtLink
          class="text-gray-500 no-underline hover:text-gray-900 dark:text-gray-400 dark:hover:text-gray-300"
          :href="`#${id}`"
          :title="text"
          :class="{ 'font-medium': activeToc == id }"
        >
          {{ text }}
        </NuxtLink>
      </li>
    </ul>
  </aside>
</template>
