<template>
  <div class="pokemon-list nes-container is-rounded">
    <ul>
      <li
        v-for="pokemon in pokemonList"
        :key="pokemon"
        class="nes-container is-rounded nes-btn"
        @click="$emit('show-pokemon', pokemon)"
      >
        <i class="nes-pokeball"></i>
        <div class="text">{{ pokemon }}</div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    pokemonList: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="postcss" scoped>
/* pokemons list */
.pokemon-list {
  @apply !bg-red-50 h-full max-h-[800px] overflow-y-auto;
}
.pokemon-list ul {
  @apply flex flex-col gap-2;
}
.pokemon-list ul li {
  @apply bg-blue-200 text-gray-900 flex flex-row !p-0 gap-2 items-center;
  @apply hover:bg-green-200;
}
.pokemon-list ul li .text {
  @apply p-4 text-lg;
}
</style>
