<template>
  <div class="nes-circle nes-container is-rounded" :class="[color, {small: small}]">
    <div v-show="reflex" :class="color" />
  </div>
</template>

<script setup>
const props = defineProps({
  color: {
    type: String,
    default: "bg-white",
  },
  reflex: {
    type: Boolean,
    default: false,
  },
  small: {
    type: Boolean,
    default: false
  }
});
</script>

<style lang="postcss" scoped>
.nes-circle {
  @apply h-24 w-24 relative hover:bg-opacity-60;
}
.nes-circle > div {
  @apply h-8 w-8 brightness-200 rounded-sm absolute top-2 left-2;
}
.nes-circle.small {
  @apply w-10 h-12;
}
.nes-circle.small > div {
  @apply w-4 h-4;
}
</style>
