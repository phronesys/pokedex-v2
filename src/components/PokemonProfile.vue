<template>
  <div class="profile nes-container is-rounded">
    <div class="pokemon-card nes-container is-dark is-rounded with-title">
      <p class="title">{{ pokemonName }}</p>
      <img
        class="w-64 h-64"
        src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/120.svg"
        alt=""
      />
    </div>
    <div class="stats nes-container bg-white is-rounded with-title">
      <h1 class="title">Stats</h1>
      <ul>
        <li v-for="stat in pokemonStats.stats" :key="stat">
          <div>{{stat.name}}</div>
          <div>{{stat.value}}</div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
let pokemonName = "Pokemon name";
import {pokemonStats} from "../controls/getPokemonStats";
</script>

<style lang="postcss" scoped>
.profile {
  @apply w-10/12 flex justify-start bg-white;
}
.stats {
  @apply w-8/12 h-64 self-center;
}
.stats ul li {
  @apply flex flex-row justify-between;
}
.pokemon-card {
  @apply bg-white min-w-max max-w-max;
}
</style>
