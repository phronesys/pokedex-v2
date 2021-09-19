<template>
  <div class="search nes-field nes-container is-rounded is-inline">
    <label for="name">Search</label>
    <input
      v-model="entry"
      @keyup="$emit('filter', entry)"
      type="text"
      placeholder="Pokémon"
      id="name"
      class="nes-input"
    />
  </div>
</template>

<script setup>
import { ref } from "vue";
let entry = ref("");
</script>

<style lang="postcss" scoped>
input {
  @apply bg-red-200 text-gray-800;
}
.search {
  @apply bg-red-600 text-white;
}
</style>
