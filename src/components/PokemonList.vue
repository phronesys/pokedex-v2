<template>
  <div class="pokemon-list nes-container is-rounded">
    <ul>
      <li
        v-for="pokemon in pokemons"
        :key="pokemon.id"
        class="nes-container is-rounded nes-btn"
      >
        <i class="nes-pokeball"></i>
        <div class="text">001 Bulbasaur</div>
      </li>
    </ul>
    <div class=""></div>
  </div>
</template>

<script setup>
import { pokemons } from "../getPokemons";
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
  @apply hover:bg-red-200;
}
.pokemon-list ul li .text {
  @apply p-4 text-lg;
}

</style>
