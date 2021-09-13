<template>
  <div class="abilities">
    <div class="nes-container is-rounded with-title">
      <h1 class="title" @click="abilityTab = !abilityTab">
        <a v-if="abilityTab">Abilities</a>
        <a v-else>Description</a>
      </h1>
      <ul v-if="abilityTab">
        <li v-for="item in 4" :key="item">
          <div>Impactrueno</div>
          <div>25/34</div>
        </li>
      </ul>
      <div class="description" v-else>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Cumque omnis odit optio! Voluptates tempora quae quisquam animi asperiores accusantium nihil!
      </div>
    </div>
  </div>
</template>

<script setup>
import {ref} from 'vue';
let abilityTab = ref(true);
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
