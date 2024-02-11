<script setup lang="ts">
import { CheckCircleIcon } from '@heroicons/vue/24/solid'
import { ClockIcon, ListBulletIcon, ChartBarIcon } from '@heroicons/vue/24/outline'


const navTitles: string[] = ['timeline', 'activities', 'progress']
</script>

<template>
  <header class="sticky top-0 z-20 flex items-center justify-between border-b-2 bg-white p-3">
    <a href="#">
      <img src="./assets/img/logo.png" alt="logo" class="h-9" srcset="" />
    </a>
    <a href="#">
      <div v-if="true" class="flex items-center gap-2 text-sm font-bold text-green-500">
        Day complete!
        <CheckCircleIcon class="h-7" />
      </div>
      <div v-else class="flex items-center gap-2">
        <div class="">Progress: <span class="font-mono">20%</span></div>
        <div class="h-3 w-3 rounded-full bg-red-600"></div>
      </div>
    </a>
  </header>
  <main>Lorem500</main>
  <nav class="fixed bottom-0 z-20 w-full bg-white text-xl">
    <ul class="flex items-center justify-around border-t text-center pt-2">
      <li v-for="title in navTitles" :key="title" class="flex-1 capitalize">
        <a class="flex flex-col" :href="`#${title}`">
          <ClockIcon v-if="title === `${navTitles[0]}`" class="h-6" />
          <ListBulletIcon v-else-if="title === `${navTitles[1]}`" class="h-6" />
          <ChartBarIcon v-else class="h-6" />
          {{ title }}
        </a>
      </li>
    </ul>
  </nav>
</template>
