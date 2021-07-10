<template>
  <header class="border-gray-200 border-b-2 p-2 h-14">
    <div class="container mx-auto flex justify-between items-center">
      <nuxt-link to="/">
        <div class="right flex justify-start items-center">
          <img class="w-8 h-8 mr-3" src="/anime.png" />
          <h1 class="text-lg font-bold text-gray-700">{{ title }}</h1>
        </div>
      </nuxt-link>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      title: 'Animes',
    }
  },
}
</script>
