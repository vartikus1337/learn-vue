<script setup lang="ts">
import type { FunctionalComponent, HTMLAttributes, VNodeProps } from 'vue'
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