<script setup lang="ts">
useHead({
  script: [
    {
      children: `localStorage.getItem("vueuse-color-scheme") == 'dark' 
    ? document.documentElement.classList.add("dark") 
    : document.documentElement.classList.remove("dark");`,
    },
  ],
});
</script>
<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>
