<template>
  <div class="container mx-auto pt-6 mb-6">
    <article v-if="post">
      <header class="flex mb-12 rounded shadow-lg p-4">
        <img class="h-64 mr-4" :src="post.media" :alt="post.title" />
        <div class="flex-auto">
          <h2 class="text-3xl font-bold text-gray-800 mb-2">
            {{ post.title }}
          </h2>
          <div class="text-xl">
            <p>Creador: {{ post.creator }}</p>
            <p>Estudio: {{ post.studio }}</p>
            <p>Género: {{ post.genres }}</p>
          </div>
        </div>
      </header>
      <nuxt-content class="text-gray-800" :document="post" />
      <StarRating :rating="post.rating" read-only="true"></StarRating>
    </article>
  </div>
</template>

<script>
import StarRating from 'vue-star-rating'
export default {
  components: {
    StarRating,
  },
  async asyncData({ $content, params }) {
    const post = await $content('anime', params.slug).fetch()
    return { post }
  },
  head() {
    return {
      title: this.post.title,
    }
  },
}
</script>

<style lang="scss">
.nuxt-content {
  h1,
  h2,
  h3,
  h4 {
    position: relative;
    font-weight: 700;
    margin-bottom: 2rem;
  }
  h1 {
    font-size: 2rem;
  }
  h2 {
    font-size: 1.75rem;
  }
  h3 {
    font-size: 1.5rem;
  }
  h4 {
    font-size: 1.25rem;
  }
  ul {
    list-style: disc;
  }
  ul,
  ol {
    margin: 1rem 0;
    padding-left: 40px;
  }
  ul,
  ol > li:last-child {
    margin-bottom: 10px;
  }
  table {
    margin-bottom: 10px;
    border-collapse: collapse;
  }
  th,
  td {
    padding: 0.5rem;
  }
  p {
    margin-bottom: 1rem;
    img {
      display: block;
    }
    img + em {
      display: block;
      margin-top: 0.5rem;
      font-size: 12px;
    }
  }
}
</style>
