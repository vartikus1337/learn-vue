<script lang="ts">
export default {
    inheritAttrs: false // Чтобы всем элементам не добавился href
}
</script>
<template>
  <li class="flex-1">
    <a v-bind="$attrs" class="flex flex-col capitalize pt-2">
      <slot></slot>
    </a>
  </li>
</template>
