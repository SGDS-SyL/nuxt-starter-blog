<script lang="ts" setup>
import { ParsedContent } from "@nuxt/content/dist/runtime/types";

defineProps<{
  article: ParsedContent; // Receive an article object to work with
}>();
</script>

<template>
  <div class="flex w-full flex-col gap-3">
    <NuxtLink :to="article._path" :title="article.title">
      <div class="mb-2 font-medium text-orange-700">
        {{ useTimeAgo(article.date).value }}
        <!-- Vueuse function that allows us to format date as time ago -->
      </div>
      <h2 class="mb-3 text-lg font-semibold hover:text-orange-700 lg:text-2xl">
        {{ article.title }}
      </h2>
      <p v-if="article.description" class="leading-6 text-gray-600">
        {{ article.description }}
      </p>
    </NuxtLink>
  </div>
</template>
