<script setup lang="ts">
import { ref } from 'vue'
import type { FunctionalComponent, HTMLAttributes, VNodeProps } from 'vue'
import { ClockIcon, ListBulletIcon, ChartBarIcon } from '@heroicons/vue/24/outline'
import { PAGE_TIMELINE, PAGE_ACTIVITIES, PAGE_PROGRESS } from './constants'
import NavItem from './NavItem.vue'

interface navItem {
  page: string
  icon: FunctionalComponent<HTMLAttributes & VNodeProps>
}

const navItems: Array<navItem> = [
  { page: PAGE_TIMELINE, icon: ClockIcon },
  { page: PAGE_ACTIVITIES, icon: ListBulletIcon },
  { page: PAGE_PROGRESS, icon: ChartBarIcon }
]

let currentPage = ref(normalizePageHash())

function normalizePageHash() {
  const hash = window.location.hash.slice(1) // Срезаем 1 символ это решётка
  if (Object.keys(navItems).includes(hash)) return hash
  window.location.hash = PAGE_TIMELINE
  return PAGE_TIMELINE
}
</script>

<template>
  <nav class="fixed bottom-0 z-20 w-full bg-white text-xl">
    <ul class="flex items-center justify-around border-t text-center">
      <NavItem
        v-for="{ page: title, icon } in navItems"
        :key="title"
        :href="`#${title}`"
        :class="{ 'pointer-events-none bg-gray-200': title == currentPage }"
        @click="currentPage = title"
      >
        <component :is="icon" class="h-6" /> {{ title }}
      </NavItem>
    </ul>
  </nav>
</template>
