<template>
  <div class="profile nes-container is-rounded">
    <div class="pokemon-card nes-container is-dark is-rounded with-title">
      <p class="title">{{ name }}</p>
      <img class="w-64 h-64" :src="sprite" :alt="name" />
    </div>
    <div class="stats nes-container bg-white is-rounded with-title is-dark">
      <h1 class="title">Stats</h1>
      <ul>
        <li v-for="stat in stats" :key="stat">
          <div v-if="stat.stat">{{ capitalize(stat.stat.name) }}</div>
          <div v-if="stat.stat">{{ stat.base_stat }}</div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: ["pokemon", "stats", "sprite", "name"],
  methods: {
    capitalize(string) {
      return string.charAt(0).toUpperCase() + string.slice(1);
    }
  }
};
</script>

<style lang="postcss" scoped>
.profile {
  @apply w-full flex justify-start bg-white;
}
.stats {
  @apply w-8/12 min-w-max h-64 self-center;
}
.stats ul li {
  @apply flex flex-row justify-between gap-4;
}
.pokemon-card {
  @apply bg-white min-w-max max-w-max;
}
</style>
