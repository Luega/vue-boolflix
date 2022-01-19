<template>
  <main>
      <ul>
          <li v-if="this.movie.length != 0">
              <Card
              v-for="(movie, index) in movies"
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
import axios from "axios";
import Card from "./Card.vue";

export default {
    name:"Main",
    components: {
        Card,
    },
    props: {
        inputText: {
            type: String,
        }
    },
    data() {
        return {
            movies: [],
            query: "https://api.themoviedb.org/3/search/movie?api_key=72c83988e48ed668d3d11346217d3feb&query=",
        }
    },
    computed: {
    },
    methods: {
        getMovies(text) {
            text = text.replace(/ /i, "+");
            axios.get(this.query + text)
            .then((result) => {
                console.log(result.data.results);
                this.movies = result.data.results;
            }) 
            .catch((error) => {
                console.log(error);
            })
        }
    }
}
</script>

<style lang="scss" scoped>

</style>