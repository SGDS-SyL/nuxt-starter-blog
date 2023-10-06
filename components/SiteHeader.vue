<script lang="ts" setup>
import { SunIcon, MoonIcon } from "@heroicons/vue/24/solid";

const isDark = useDark();
const toggleDark = useToggle(isDark);
</script>

<template>
  <header>
    <div class="mx-auto w-24">
      <NuxtLink to="/">
        <ClientOnly>
          <img
            :src="`/images/${isDark ? 'logo-dark.svg' : 'logo.svg'}`"
            alt="Logo"
            width="100"
            height="100"
          />
        </ClientOnly>
      </NuxtLink>
    </div>
    <div class="mx-auto my-5 max-w-xl text-center">
      <div class="font-semibold text-xl mb-2">
        An open source content by
        <NuxtLink class="text-orange-600" to="https://sgds.app">SGDS</NuxtLink>
      </div>
      This is a starter blog created with Nuxt 3 Content and Tailwind CSS.<br />
      🌟 Check out this
      <NuxtLink
        class="underline"
        to="https://sgds.app/articles/create-a-nuxt-3-content-blog-with-tailwind-css-in-one-hour"
      >
        tutorial here to learn how we build it step by step.
      </NuxtLink>
      🌈
    </div>
    <div class="max-w-lg mx-auto flex justify-center my-3">
      <button
        class="rounded-md p-1.5 transition-colors hover:bg-gray-100 dark:text-gray-200 dark:hover:bg-gray-800"
        aria-label="Change color mode"
        @click="toggleDark()"
      >
        <client-only>
          <!-- This is to make sure the icon is render only in client-side -->
          <MoonIcon class="h-5 w-5" v-if="isDark" />
          <SunIcon class="h-5 w-5" v-else />
        </client-only>
      </button>
    </div>
  </header>
</template>
