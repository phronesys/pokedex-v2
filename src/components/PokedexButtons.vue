<template>
  <div class="buttons">
    <ness-circle small color="bg-gray-700" />
    <div class="mini-buttons">
      <div class="mini-button bg-red-400"></div>
      <div class="mini-button bg-indigo-400"></div>
    </div>
    <the-cruz class="hover:opacity-90" />
  </div>
</template>

<script setup>
import TheCruz from "./TheCruz.vue";
import NessCircle from "./NessCircle.vue";
</script>

<style lang="postcss" scoped>
.buttons {
  @apply h-[400px] w-full flex flex-row justify-between items-center px-28;
}
.mini-buttons {
  @apply flex flex-row gap-8 self-start mt-14;
}
.mini-button {
  @apply h-4 w-16 rounded border-2 border-current hover:bg-opacity-70;
}

</style>
