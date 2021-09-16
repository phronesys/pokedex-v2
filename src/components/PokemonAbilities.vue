<template>
  <div class="abilities">
    <div class="nes-container is-rounded with-title">
      <h1 class="title">Abilities</h1>
      <ul>
        <slot />
      </ul>
    </div>
  </div>
</template>

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
