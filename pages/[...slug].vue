<script setup lang="ts">
const { path } = useRoute();

const { data: article } = await useAsyncData(`article-${path}`, () =>
  queryContent(path).count()
);

if (!article.value) {
  throw createError({ statusCode: 404 });
}
</script>
<template>
  <main class="my-20 max-w-5xl mx-auto">
    <ContentDoc v-slot="{ doc }">
      <ArticleDetails :article="doc" class="mb-5" />
      <!-- Update code from below -->
      <div
        class="my-8 lg:my-16 flex flex-col gap-10 lg:flex-row-reverse lg:items-start lg:gap-20 lg:px-4"
      >
        <ArticleTableOfContents
          :toc="doc.body.toc?.links ?? []"
          class="top-14 h-auto lg:sticky lg:w-1/4"
        />

        <ContentRenderer :value="doc" class="lg:w-3/4" />
      </div>
    </ContentDoc>
  </main>
</template>
