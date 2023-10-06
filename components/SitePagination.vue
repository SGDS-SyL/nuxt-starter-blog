<script lang="ts" setup>
defineProps<{
  currentPage: number;
  totalPages: number;
  link: string;
}>();
</script>

<template>
  <ul class="mx-auto gap-3 lg:flex justify-center not-prose">
    <li v-for="page in totalPages" :key="page">
      <NuxtLink
        :to="`${link}?page=${page}`"
        :class="
          currentPage === page
            ? 'bg-gray-100 dark:bg-gray-800 dark:text-gray-200'
            : ''
        "
        class="inline-flex rounded-md px-3 py-1 hover:bg-gray-200"
      >
        {{ page }}
      </NuxtLink>
    </li>
  </ul>
</template>
