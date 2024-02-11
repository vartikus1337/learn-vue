<script setup lang="ts">
import TheHeader from '@/components/TheHeader.vue'
import TheNav from '@/components/TheNav.vue'
import TheActivities from '@/pages/TheActivities.vue'
import TheTimeline from '@/pages/TheTimeline.vue'
import TheProgress from '@/pages/TheProgress.vue'
import { PAGE_ACTIVITIES, PAGE_TIMELINE, PAGE_PROGRESS } from './components/constants'
import { ref } from 'vue'

let currentPage = ref(normalizePageHash())

function normalizePageHash() {
  const hash = window.location.hash.slice(1) // Срезаем 1 символ это решётка
  if (Object.keys([PAGE_ACTIVITIES, PAGE_TIMELINE, PAGE_PROGRESS]).includes(hash)) return hash
  window.location.hash = PAGE_TIMELINE
  return PAGE_TIMELINE
}
</script>

<template>
  <TheHeader />
  <main>
    <TheActivities v-show="currentPage === PAGE_ACTIVITIES" />
    <TheTimeline v-show="currentPage === PAGE_TIMELINE" />
    <TheProgress v-show="currentPage === PAGE_PROGRESS" />
  </main>
  <TheNav :current-page="currentPage" @navigate="currentPage = $event" />
</template>
