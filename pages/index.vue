<script lang="ts" setup>
useSeoMeta({
  //A Nuxt composable to set our page title and description
  title: "Starter blog created with Nuxt 3 Content and Tailwind CSS",
  description: "An open source content by SGDS written by SyL.",
});

const route = useRoute(); //A Nuxt composable for us to retrieve the page number from the URL
const perPage: number = 1;
const pageNo = ref<number>(Number(route.query.page ?? 1)); //Retrive the page number from the URL

const { data: articlesCount } = await useAsyncData(
  "articles-count",
  () =>
    queryContent() //A Nuxt composable that to fetch our articles
      .count() //Get the total article counts
);

const totalPages: number =
  articlesCount && articlesCount.value! > 0
    ? Math.ceil(articlesCount.value! / perPage)
    : 0; //Calculate our total pages for pagination

const { data: articles } = await useAsyncData(
  "articles",
  () =>
    queryContent()
      .sort({ date: -1 }) //Sort our articles by descending date
      .limit(perPage) //Limit and skip our articles for pagination
      .skip(perPage * (pageNo.value - 1))
      .find(),
  {
    watch: [pageNo], //Watch for the page no changes and refresh our query
  }
);

watch(
  () => route.query.page, //Watch for the page no and update it
  async (page) => {
    pageNo.value = Number(page);
  }
);
</script>

<template>
  <div class="my-24">
    <div class="mx-auto mb-20 flex max-w-3xl flex-col justify-start gap-12">
      <ArticleList v-for="article in articles" :article="article" />
    </div>
    <SitePagination
      v-if="totalPages"
      :per-page="perPage"
      :totalPages="totalPages"
      :currentPage="pageNo"
      link="/"
    />
  </div>
</template>
