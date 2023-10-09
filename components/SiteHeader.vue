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
    <div class="max-w-lg mx-auto flex justify-center my-3 gap-3 items-center">
      <button
        class="rounded-md p-1.5 transition-colors hover:bg-gray-100 dark:text-gray-200 dark:hover:bg-gray-800"
        aria-label="Change color mode"
        @click="toggleDark()"
      >
        <client-only>
          <!-- This is to make sure the icon is render only in client-side -->
          <MoonIcon class="h-6 w-6" v-if="isDark" />
          <SunIcon class="h-6 w-6" v-else />
        </client-only>
      </button>

      <NuxtLink
        to="https://github.com/SGDS-SyL/nuxt-starter-blog"
        :external="true"
        target="_blank"
        class="rounded-md p-1.5 transition-colors hover:bg-gray-100 dark:text-gray-200 dark:hover:bg-gray-800"
      >
        <svg
          class="w-6 h-6 dark:fill-gray-200"
          aria-hidden="true"
          viewBox="0 0 16 16"
          version="1.1"
          data-view-component="true"
        >
          <path
            d="M8 0c4.42 0 8 3.58 8 8a8.013 8.013 0 0 1-5.45 7.59c-.4.08-.55-.17-.55-.38 0-.27.01-1.13.01-2.2 0-.75-.25-1.23-.54-1.48 1.78-.2 3.65-.88 3.65-3.95 0-.88-.31-1.59-.82-2.15.08-.2.36-1.02-.08-2.12 0 0-.67-.22-2.2.82-.64-.18-1.32-.27-2-.27-.68 0-1.36.09-2 .27-1.53-1.03-2.2-.82-2.2-.82-.44 1.1-.16 1.92-.08 2.12-.51.56-.82 1.28-.82 2.15 0 3.06 1.86 3.75 3.64 3.95-.23.2-.44.55-.51 1.07-.46.21-1.61.55-2.33-.66-.15-.24-.6-.83-1.23-.82-.67.01-.27.38.01.53.34.19.73.9.82 1.13.16.45.68 1.31 2.69.94 0 .67.01 1.3.01 1.49 0 .21-.15.45-.55.38A7.995 7.995 0 0 1 0 8c0-4.42 3.58-8 8-8Z"
          ></path>
        </svg>
      </NuxtLink>

      <NuxtLink
        to="https://twitter.com/SGDS_SyL"
        :external="true"
        target="_blank"
        class="rounded-md p-1.5 transition-colors hover:bg-gray-100 dark:text-gray-200 dark:hover:bg-gray-800"
      >
        <svg
          class="w-7 h-7 dark:fill-gray-200"
          xmlns:svg="http://www.w3.org/2000/svg"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          version="1.1"
          id="svg5"
          x="0px"
          y="0px"
          viewBox="0 0 1668.56 1221.19"
          style="enable-background: new 0 0 1668.56 1221.19"
          xml:space="preserve"
        >
          <g id="layer1" transform="translate(52.390088,-25.058597)">
            <path
              id="path1009"
              d="M283.94,167.31l386.39,516.64L281.5,1104h87.51l340.42-367.76L984.48,1104h297.8L874.15,558.3l361.92-390.99   h-87.51l-313.51,338.7l-253.31-338.7H283.94z M412.63,231.77h136.81l604.13,807.76h-136.81L412.63,231.77z"
            />
          </g>
        </svg>
      </NuxtLink>
    </div>
  </header>
</template>
