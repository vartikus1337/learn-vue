<script setup lang="ts">
import { CheckCircleIcon } from '@heroicons/vue/24/solid'
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
  <main>Lorem300</main>
  <nav class="fixed bottom-0 z-20 bg-white text-3xl">nav</nav>
</template>
