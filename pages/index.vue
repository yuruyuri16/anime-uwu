<template>
  <div class="container mx-auto">
    <section class="grid grid-cols-3 gap-4 pt-12">
      <article
        v-for="(post, $index) in posts"
        :key="`post-${$index}`"
        class="border-2 border-gray-300 max-w-sm rounded overflow-hidden shadow-lg flex flex-col"
      >
        <img class="object-contain h-48" :src="post.media" alt="post.title" />
        <div class="px-6 py-4 flex-2">
          <h3>{{ post.title }}</h3>
          <p class="text-gray-700 text-base">
            {{ post.description }}
          </p>
        </div>
        <footer class="p-4">
          <nuxt-link :to="post.path" class="font-bold text-xl mb-2">
            <button type="button" class="font-bold py-2 px-4 rounded bg-gray-300">Ver más</button>
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
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}
</style>
