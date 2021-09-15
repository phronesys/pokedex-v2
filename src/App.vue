<template>
  <section>
    <top-bar></top-bar>
    <div class="main">
      <div class="left">
        <div class="nes-container is-rounded">
          <pokemon-profile :pokemon="pokemon">
          </pokemon-profile>
          <pokedex-buttons></pokedex-buttons>
          <pokemon-abilities :pokemon="pokemon"></pokemon-abilities>
        </div>
      </div>
      <div class="right">
        <div>
          <pokemon-search></pokemon-search>
          <pokemon-list @show-pokemon="selectPokemon" :pokemonList="pokemonList"></pokemon-list>
        </div>
      </div>
    </div>
  </section>
</template>
<script>
import NessCircle from "./components/NessCircle.vue";
import PokemonSearch from "./components/PokemonSearch.vue";
import PokemonList from "./components/PokemonList.vue";
import TopBar from "./components/TopBar.vue";
import PokemonProfile from "./components/PokemonProfile.vue";
import PokemonAbilities from "./components/PokemonAbilities.vue";
import PokedexButtons from "./components/PokedexButtons.vue";

export default {
  components: {
    NessCircle,
    PokemonSearch,
    PokemonList,
    TopBar,
    PokemonProfile,
    PokemonAbilities,
    PokedexButtons,
  },
  data: () => ({
    pokemonList: null,
    selected: 1,
    pokemon: null,
  }),
  methods: {
    selectPokemon(index){
      this.selected = index + 1;
    },
    async getPokemonList() {
      return await fetch(`https://pokeapi.co/api/v2/pokemon/?limit=151`)
        .then((response) => response.json())
        .then((data) => data.results)
        .catch((e) => console.log(e));
    },
    async getPokemon(index) {
      return await fetch(`https://pokeapi.co/api/v2/pokemon/${index}`)
        .then((response) => response.json())
        .catch((e) => console.log(e));
    },
    capitalize(string){
      return string.charAt(0).toUpperCase() + string.slice(1)
    }
  },
  async mounted() {
    let pokemonList = await this.getPokemonList();
    this.pokemonList = pokemonList.map((pokemon) => {
      return this.capitalize(pokemon.name)
    });
    this.pokemon = await this.getPokemon(this.selected);
    console.log(this.pokemon);
  },
};
</script>

<style lang="postcss">
@import url("https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap");
#app {
  font-family: "Press Start 2P", cursive, Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  @apply bg-indigo-200;
}
/* layout */
section {
  @apply h-screen w-screen flex flex-col;
}
.main {
  @apply flex flex-row gap-4 h-5/6 p-4 overflow-x-auto;
}
.main .left {
  @apply w-1/2 min-w-[800px] max-w-[1000px] max-h-[800px];
}
.main .left > div {
  @apply h-full w-full flex flex-col items-center justify-between gap-2 bg-red-600;
}
.main .right {
  @apply w-1/2 min-w-[600px] max-w-[1000px] max-h-[1000px];
}
.main .right > div {
  @apply h-full flex flex-col gap-1;
}
/* scrollbar */
::-webkit-scrollbar {
  @apply w-6 rounded-md;
}
::-webkit-scrollbar-track {
  @apply bg-white rounded-md;
  border: 6px solid rgba(0, 0, 0, 0.8);
}
::-webkit-scrollbar-thumb {
  @apply bg-red-500 rounded-md shadow-lg;
  border: 6px solid rgba(0, 0, 0, 0.5);
}
</style>
