<template>
  <div class="container mx-auto">
    <div class="flex flex-col items-center px-4">
      <h1 class="title uppercase">
        Top 10 animes para ver cuando estés aburrido
      </h1>
    </div>
    <section
      class="
        grid grid-cols-1
        md:grid-cols-2
        lg:grid-cols-3
        xl:grid-cols-4
        gap-4
        pt-12
        px-4
      "
    >
      <article
        v-for="(post, $index) in posts"
        :key="`post-${$index}`"
        class="
          border-2 border-gray-300
          rounded
          overflow-hidden
          shadow-lg
          flex flex-col
        "
      >
        <img class="object-contain h-48" :src="post.media" :alt="post.title" />
        <div class="px-6 py-4 flex-2">
          <h3 class="font-bold text-lg">{{ post.title }}</h3>
        </div>
        <footer class="p-4 ml-auto">
          <nuxt-link :to="post.path" class="font-bold text-lg mb-2">
            <button
              type="button"
              class="font-bold py-2 px-4 rounded bg-gray-300"
            >
              Ver más
            </button>
          </nuxt-link>
        </footer>
      </article>
    </section>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const posts = await $content('anime').fetch()
    return { posts }
  },
}
</script>

<style>
.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 700;
  font-size: 30px;
  color: #35495e;
  letter-spacing: 1px;
}
</style>
