<template>
  <section>
    <top-bar></top-bar>
    <div class="main">
      <div class="left">
        <div class="nes-container is-rounded">
          <pokemon-profile
            :stats="pokemonStats"
            :sprite="pokemonSprite"
            :name="pokemonName"
          >
          </pokemon-profile>
          <pokedex-buttons></pokedex-buttons>
          <pokemon-abilities>
            <li
              class="ability"
              v-for="(info, index) in abilitiesInfo"
              :key="info"
            >
              <div class="name">
                {{ abilitiesName[index] }}
              </div>
              <div class="info">
                {{ info }}
              </div>
            </li>
          </pokemon-abilities>
        </div>
      </div>
      <div class="right">
        <div>
          <pokemon-search @filter="filterPokemon"></pokemon-search>
          <pokemon-list
            @show-pokemon="selectPokemon"
            :pokemonList="pokemonList"
          ></pokemon-list>
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
    tempList: null,
    selected: 1,
    pokemon: null,
    abilitiesInfo: [],
    abilitiesName: [],
  }),
  computed: {
    pokemonStats() {
      return this.pokemon ? this.pokemon.stats : "Loading";
    },
    pokemonSprite() {
      return this.pokemon ? this.pokemon.sprites.front_default : "Loading";
    },
    pokemonName() {
      return this.pokemon ? this.capitalize(this.pokemon.name) : "Loading";
    },
  },
  methods: {
    filterPokemon(entry) {
      if (!entry) return this.resetList();
      this.pokemonList = this.pokemonList.filter((pokemon) =>
        pokemon.toLowerCase().includes(entry.toLowerCase())
      );
    },
    resetList() {
      this.pokemonList = this.tempList;
    },
    async selectPokemon(name) {
      this.selected = this.pokemonIndexByName(name) + 1;
      await this.updatePokemon();
    },
    pokemonIndexByName(name) {
      console.log(this.tempList, name);
      return this.tempList.indexOf(name);
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
    async getAbilityInfo(url) {
      return await fetch(url)
        .then((response) => response.json())
        .then((data) =>
          data.effect_entries.filter((entry) => entry.language.name === "en")
        )
        .then((entry) => entry[0].short_effect)
        .catch((e) => console.log(e));
    },
    capitalize(string) {
      return string.charAt(0).toUpperCase() + string.slice(1);
    },
    async updatePokemon() {
      this.pokemon = await this.getPokemon(this.selected);
      this.abilitiesInfo = []; /* clear previous pokemon abilities */
      this.abilitiesName = this.pokemon.abilities.map((ability) =>
        this.capitalize(ability.ability.name)
      );
      /* get all ability info from the pokemon ability url */
      await this.pokemon.abilities.map(
        async (ability) =>
          await this.getAbilityInfo(ability.ability.url).then((data) =>
            this.abilitiesInfo.push(data)
          )
      );
    },
  },
  async mounted() {
    let pokemonList = await this.getPokemonList();
    this.pokemonList = pokemonList.map((pokemon) => {
      return this.capitalize(pokemon.name);
    });
    this.tempList = this.pokemonList;
    await this.updatePokemon();
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
  @apply bg-indigo-500 rounded-md shadow-lg;
  border: 6px solid rgba(0, 0, 0, 0.5);
}

/* abilities */
.ability .name {
  @apply bg-green-300 max-w-max py-1 px-2 rounded-sm mb-2;
}
.ability .info {
  @apply text-sm;
}
</style>
