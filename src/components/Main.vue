<template>
  <main>
      <button @click="getMovies(inputText)">

      </button>
  </main>
</template>

<script>
import axios from "axios";

export default {
    name:"Main",
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
            console.log(text);
            axios.get(this.query + text)
            .then((result) => {
                console.log(result.data.results);
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