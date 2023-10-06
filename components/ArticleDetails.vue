<script lang="ts" setup>
import moment from "moment";
import { ParsedContent } from "@nuxt/content/dist/runtime/types";

/* An article object will be passed over for us to use and it will 
contain our Front-matter data including the author and date. */
const props = defineProps<{
  article: ParsedContent;
}>();

// Format the article date using the moment package we installed
const publishedOn = computed(() => {
  return props.article.date
    ? moment(props.article.date).format("DD MMM YYYY")
    : null;
});
</script>

<template>
  <div class="flex justify-between gap-12 lg:justify-start">
    <div v-if="article.author">
      <div class="mb-1 text-sm font-medium text-gray-500">Written by</div>
      <div class="text-md font-medium text-gray-900 dark:text-gray-400">
        {{ article.author }}
      </div>
    </div>
    <div v-if="publishedOn">
      <div class="mb-1 text-sm font-medium text-gray-500">Published on</div>
      <div class="text-md font-medium text-gray-900 dark:text-gray-400">
        {{ publishedOn }}
      </div>
    </div>
  </div>
</template>
