<script setup lang="ts">
import type { FunctionalComponent, HTMLAttributes, VNodeProps } from 'vue'
import { ClockIcon, ListBulletIcon, ChartBarIcon } from '@heroicons/vue/24/outline'
import { PAGE_TIMELINE, PAGE_ACTIVITIES, PAGE_PROGRESS } from './constants'
import NavItem from './NavItem.vue'

defineProps(['currentPage'])

const emit = defineEmits(['navigate'])

interface navItem {
  page: string
  icon: FunctionalComponent<HTMLAttributes & VNodeProps>
}

const navItems: Array<navItem> = [
  { page: PAGE_TIMELINE, icon: ClockIcon },
  { page: PAGE_ACTIVITIES, icon: ListBulletIcon },
  { page: PAGE_PROGRESS, icon: ChartBarIcon }
]
</script>

<template>
  <nav class="fixed bottom-0 z-20 w-full bg-white text-xl">
    <ul class="flex items-center justify-around border-t text-center">
      <NavItem
        v-for="{ page: title, icon } in navItems"
        :key="title"
        :href="`#${title}`"
        :class="{ 'pointer-events-none bg-gray-200': title == currentPage }"
        @click="emit('navigate', title)"
      >
        <component :is="icon" class="h-6" /> {{ title }}
      </NavItem>
    </ul>
  </nav>
</template>
