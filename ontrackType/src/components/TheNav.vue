<script setup lang="ts">
import { ref } from 'vue'
import type { FunctionalComponent, HTMLAttributes, VNodeProps } from 'vue'
import { ClockIcon, ListBulletIcon, ChartBarIcon } from '@heroicons/vue/24/outline'
import NavItem from './NavItem.vue'

interface navItem {
  title: string
  icon: FunctionalComponent<HTMLAttributes & VNodeProps>
}

const navItems: Array<navItem> = [
  { title: 'timeline', icon: ClockIcon },
  { title: 'activities', icon: ListBulletIcon },
  { title: 'progress', icon: ChartBarIcon }
]

let currentPage = ref('timeline');
</script>

<template>
  <nav class="fixed bottom-0 z-20 w-full bg-white text-xl">
    <ul class="flex items-center justify-around border-t text-center">
      <NavItem 
        v-for="{ title, icon } in navItems" 
        :key="title" 
        :href="`#${title}`"
        :class="{'bg-gray-200 pointer-events-none': title == currentPage}"
        @click="currentPage = title"
      >
        <component :is="icon" class="h-6" /> {{ title }}
      </NavItem>
    </ul>
  </nav>
</template>
