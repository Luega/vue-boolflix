<template>
  <main>
      <ul>
          <li>
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
      <button @click="consoleLog(movies)">clicca</button>
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
        consoleLog(string) {
         console.log(string);
         if(this.movie) {
                this.moviesNew = this.movies.map(movie => ({ title: movie.title, original_title: movie.original_title, original_language: movie.original_language, vote_average:movie.vote_average }));
                return this.moviesNew
            } else {
                this.moviesNew = null;
                return this.moviesNew
            }
        },
    },
    // computed: {
    //     createArray() {
    //         if(this.movie == null) {
    //             this.moviesNew = this.movies.map(movie => ({ title: movie.title, original_title: movie.original_title, original_language: movie.original_language, vote_average:movie.vote_average }));
    //             return this.moviesNew
    //         } else {
    //             this.moviesNew = null;
    //             return this.moviesNew
    //         }
    //     }
    // },

    // mounted() {
    //     this.$nextTick(() => {
    //         if(this.movie == null) {
    //                 this.moviesNew = this.movies.map(movie => ({ title: movie.title, original_title: movie.original_title, original_language: movie.original_language, vote_average:movie.vote_average }));
    //                 return this.moviesNew
    //             } else {
    //                 this.moviesNew = null;
    //                 return this.moviesNew
    //             }
    //     })
    // }
}
</script>

<style lang="scss" scoped>

</style>