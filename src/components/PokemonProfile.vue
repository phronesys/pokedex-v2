<template>
  <div class="profile nes-container is-rounded">
    <div class="pokemon-card nes-container is-dark is-rounded with-title">
      <p class="title">{{ pokemonName }}</p>
      <img class="w-64 h-64" :src="pokemonSprite" :alt="pokemonName" />
    </div>
    <div class="stats nes-container bg-white is-rounded with-title">
      <h1 class="title">Stats</h1>
      <ul>
        <li  v-for="stat in pokemonStats" :key="stat">
          <div>{{ stat }}</div>
          <div>{{ stat}}</div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: ["pokemon"],
  computed: {
    pokemonName() {
      return this.pokemon ? this.capitalize(this.pokemon.name) : "Loading";
    },
    pokemonSprite() {
      return this.pokemon ? this.pokemon.sprites.front_default : "Loading";
    },
    pokemonStats() {
      return this.pokemon ? this.pokemon.stats : "Loading";
    },
  },
  methods: {
    capitalize(string) {
      return string.charAt(0).toUpperCase() + string.slice(1);
    },
  },
};
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
