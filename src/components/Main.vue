<template>
  <main>
      <ul>
          <li>
              <Card
              v-for="(movie, index) in this.movies"
              :key="index"
              :title="movies.title"
              :original_title="movies.original_title"
              :original_language="movies.original_language"
              :vote_average="movies.vote_average"
              />
          </li>
      </ul>
  </main>
</template>

<script>
import Card from "./Card.vue";

export default {
    name:"Main",
    components: {
        Card,
    },
    props: {
        movies: {
            type: Array,
        }
    },
}
</script>

<style lang="scss" scoped>

</style>