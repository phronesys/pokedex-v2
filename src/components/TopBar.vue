<template>
  <div class="topbar">
    <ness-circle color="bg-indigo-600" reflex />
    <div class="flex flex-row !gap-2">
      <ness-circle color="bg-yellow-300" reflex small />
      <ness-circle color="bg-green-400" reflex small />
      <ness-circle color="bg-red-300" reflex small />
    </div>
  </div>
</template>

<script setup>
import NessCircle from "./NessCircle.vue";
</script>

<style lang="postcss" scoped>
.topbar {
  @apply w-full h-36 pl-14 flex flex-row gap-20 justify-start items-start pt-4 bg-red-600 shadow-xl border-b-4 border-gray-800;
}
</style>
