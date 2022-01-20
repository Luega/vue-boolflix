<template>
  <main>
      <ul>
          <li v-for="(movie, index) in movies" :key="index + movie.id">
              <h1>{{ movie.title }}</h1>
              <div>{{ movie.original_title }}</div>
              <div>{{ movie.original_language }}</div>
              <div>{{ movie.vote_average }}</div>
          </li>
      </ul>
  </main>
</template>

<script>
// import Card from "./Card.vue";

export default {
    name:"Main",
    components: {
        // Card,
    },
    data() {
        return {
            moviesNew: [],
        }
    },
    props: {
        movies: {
            type: Array,
        }
    },
    methods: {
     
    },
    
}
</script>

<style lang="scss" scoped>
h1 {
    color: red;
}
</style>