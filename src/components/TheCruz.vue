<template>
  <div class="cruz">
    <div class="stick horizontal"></div>
    <div class="stick vertical"></div>
  </div>
</template>

<script setup></script>

<style lang="postcss" scoped>
.cruz {
  @apply border-4 border-black relative w-32 h-32 rounded-2xl bg-gray-700;
}
.stick {
  @apply bg-gray-900 shadow-2xl rounded border-4 border-black;
  @apply absolute transform -translate-x-1/2 -translate-y-1/2 top-1/2 left-1/2;
}
.stick.horizontal {
  @apply w-32 h-10;
}
.stick.vertical {
  @apply w-10 h-32;
}
</style>
