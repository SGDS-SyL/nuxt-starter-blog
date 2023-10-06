<template>
  <main class="my-20 max-w-5xl mx-auto">
    <ContentDoc v-slot="{ doc }">
      <!-- Component by Nuxt content to fetche and provide us our article to use as doc -->
      <ArticleDetails :article="doc" class="mb-5" />
      <!-- Our ArticleDetails component -->
      <ContentRenderer :value="doc" />
      <!-- Component by Nuxt content to render our article -->
    </ContentDoc>
  </main>
</template>
