<script setup lang="ts">
import { CheckCircleIcon } from '@heroicons/vue/24/solid'
</script>
<template>
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
</template>
