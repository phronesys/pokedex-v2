<script setup></script>
<template>
  <div class="h-screen w-screen flex flex-col">
    <div class="topbar">
      <div
        class="
          h-24
          w-24
          ml-6
          relative
          rounded-full
          bg-blue-500
          border-4 border-white
          shadow-xl
        "
      >
        <div
          class="bg-blue-200 rounded-full h-8 w-8 absolute top-3 left-3"
        ></div>
      </div>
      <div
        class="flex flex-row items-center justify-center gap-2 self-start mt-6"
      >
        <div
          class="h-8 w-8 rounded-full bg-red-700 border-2 shadow-xl relative"
        >
          <div
            class="bg-red-300 rounded-full h-2 w-2 absolute top-1.5 left-1.5"
          ></div>
        </div>
        <div
          class="h-8 w-8 rounded-full bg-yellow-500 border-2 shadow-xl relative"
        >
          <div
            class="bg-yellow-100 rounded-full h-2 w-2 absolute top-1.5 left-1.5"
          ></div>
        </div>
        <div
          class="h-8 w-8 rounded-full bg-green-400 border-2 shadow-xl relative"
        >
          <div
            class="bg-green-200 rounded-full h-2 w-2 absolute top-1.5 left-1.5"
          ></div>
        </div>
      </div>
    </div>
    <div class="flex flex-row gap-4 h-5/6 p-4">
      <div class="w-1/2">
        <div
          class="
            nes-container
            bg-red-600
            is-rounded
            h-full
            w-full
            flex flex-col
            items-center
            justify-between
            gap-2
          "
        >
          <div
            class="
              nes-container
              is-rounded
              w-10/12
              flex
              justify-center
              bg-white
            "
          >
            <div
              class="
                nes-container
                is-dark is-rounded
                bg-white
                min-w-max
                max-w-max
                flex
                items-center
                justify-center
              "
            >
              <img
                class="w-64 h-64"
                src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/120.svg"
                alt=""
              />
            </div>
          </div>
          <div class="flex flex-row h-full w-10/12">
            <div
              class="nes-container bg-white is-rounded with-title w-8/12 h-full"
            >
              <h1 class="title">Stats</h1>
              <ul class="stats-list">
                <li>
                  <div>HP:</div>
                  <div>25</div>
                </li>
                <li>
                  <div>ATK:</div>
                  <div>34</div>
                </li>
                <li>
                  <div>DEF:</div>
                  <div>28</div>
                </li>
                <li>
                  <div>S-ATK:</div>
                  <div>12</div>
                </li>
                <li>
                  <div>S-DEF:</div>
                  <div>23</div>
                </li>
                <li>
                  <div>SPD:</div>
                  <div>6</div>
                </li>
              </ul>
            </div>
            <div
              class="nes-container bg-white is-rounded with-title h-full w-full"
            >
              <h1 class="title">Abilities</h1>
              <ul>
                <li>
                  <div>Impactrueno</div>
                  <div>25/34</div>
                </li>
                <li>
                  <div>Impactrueno</div>
                  <div>25/34</div>
                </li>
                <li>
                  <div>Impactrueno</div>
                  <div>25/34</div>
                </li>
                <li>
                  <div>Impactrueno</div>
                  <div>25/34</div>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class="w-1/2 h-full flex flex-col gap-4">
        <div
          class="
            bg-red-600
            nes-field nes-container
            is-rounded is-inline
            text-white
          "
        >
          <label for="name">Search</label>
          <input
            type="text"
            id="name"
            class="nes-input bg-red-200 text-gray-800"
          />
        </div>
        <div class="pokemon-list nes-container is-rounded">
          <ul>
            <li
              v-for="pokemon in pokemons"
              :key="pokemon.id"
              class="
                nes-container
                is-rounded
                !p-0
                gap-2
                items-center
                !bg-blue-200
              "
            >
              <i class="nes-pokeball"></i>
              <div class="text">001 Bulbasaur</div>
            </li>
          </ul>
          <div class=""></div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
const pokemons = [
  {
    name: "000 Pokemon",
    id: "123456789",
  },
  {
    name: "000 Pokemon",
    id: "123456789",
  },
  {
    name: "000 Pokemon",
    id: "123456789",
  },
  {
    name: "000 Pokemon",
    id: "123456789",
  },
  {
    name: "000 Pokemon",
    id: "123456789",
  },
  {
    name: "000 Pokemon",
    id: "123456789",
  },
  {
    name: "000 Pokemon",
    id: "123456789",
  },
  {
    name: "000 Pokemon",
    id: "123456789",
  },
  {
    name: "000 Pokemon",
    id: "123456789",
  },
];
</script>

<style lang="postcss">
@import url("https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap");
#app {
  font-family: "Press Start 2P", cursive, Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  @apply bg-indigo-200;
}
.topbar {
  @apply w-full h-36 flex flex-row gap-8 justify-start items-center bg-red-600 shadow-xl border-b-4 border-red-800;
}
.pokemon-list {
  @apply !bg-red-50 h-full max-h-[800px] overflow-y-scroll;
}
.pokemon-list ul {
  @apply flex flex-col gap-2;
}
.pokemon-list ul li {
  @apply bg-white text-gray-900 flex flex-row;
}
.pokemon-list ul li .text {
  @apply p-4 text-lg;
}
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

.stats-list li {
  @apply flex flex-row justify-between;
}
</style>
