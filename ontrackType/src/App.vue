<script setup lang="ts">
import type { FunctionalComponent, HTMLAttributes, VNodeProps } from 'vue'
import { CheckCircleIcon } from '@heroicons/vue/24/solid'
import { ClockIcon, ListBulletIcon, ChartBarIcon } from '@heroicons/vue/24/outline'

interface navItem {
  title: string
  icon: FunctionalComponent<HTMLAttributes & VNodeProps>
}

const navItems: Array<navItem> = [
  { title: 'timeline', icon: ClockIcon },
  { title: 'activities', icon: ListBulletIcon },
  { title: 'progress', icon: ChartBarIcon }
]
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
    <ul class="flex items-center justify-around border-t pt-2 text-center">
      <li v-for="{ title, icon } in navItems" :key="title" class="flex-1">
        <a class="flex flex-col capitalize" :href="`#${title}`">
          <component :is="icon" class="h-6" /> {{ title }}
        </a>
      </li>
    </ul>
  </nav>
</template>
