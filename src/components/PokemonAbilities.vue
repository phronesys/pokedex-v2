<template>
  <div class="abilities">
    <div class="nes-container is-rounded with-title">
      <h1 class="title" @click="abilityTab = !abilityTab">
        <a :class="{ 'brightness-50': !abilityTab }"> Abilities </a>
        <a :class="{ 'brightness-50': abilityTab }">Description</a>
      </h1>
      <ul v-if="abilityTab">
        <li v-for="ability in pokemonAbilities" :key="ability">
          {{ ability }}
        </li>
      </ul>
      <div class="description" v-else>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Cumque omnis
        odit optio! Voluptates tempora quae quisquam animi asperiores
        accusantium nihil!
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['pokemon'],
  data: () => ({
    abilityTab: true,
  }),
  computed: {
    pokemonAbilities(){
      return this.pokemon ? this.pokemon.abilities : 'Loading';
    }
  }
};
</script>

<style lang="postcss" scoped>
.abilities {
  @apply flex flex-row h-[200px] w-10/12;
}
.abilities .nes-container {
  @apply bg-white h-[200px] w-full;
}
.abilities .nes-container ul {
  @apply flex flex-row flex-wrap gap-x-16 gap-y-8 ml-16;
}
.abilities .nes-container h1 {
  @apply space-x-4 select-none;
}
.abilities .nes-container h1 a {
  @apply border-4 border-gray-800 text-gray-800 bg-white p-2;
}
</style>
