<script setup lang="ts">
defineProps({
  error: Object,
});

function handleError() {
  clearError({ redirect: "/" });
}
</script>

<template>
  <NuxtLayout>
    <div class="container prose mx-auto my-16 text-center dark:prose-invert">
      <h1>Error {{ error?.statusCode }}</h1>
      <p class="mb-2">{{ error?.message }}</p>
      <p class="mt-2">It looks like there's an error 😱</p>

      <button
        @click.prevent="handleError"
        class="rounded-lg px-6 py-3 transition-colors hover:bg-gray-100 dark:hover:bg-gray-800"
      >
        Go back to home
      </button>
    </div>
  </NuxtLayout>
</template>
