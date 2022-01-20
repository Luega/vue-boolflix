<template>
  <main>
      <ul>  
        <Card 
        v-for="(movie, index) in movies"
        :key="index + movie.id"
        :title="movie.title"
        :original_title="movie.original_title"
        :original_language="movie.original_language"
        :vote_average="movie.vote_average"
        :id="movie.id"
        />
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

</style>