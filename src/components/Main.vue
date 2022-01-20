<template>
  <main>
      <ul>
          <li v-for="(movie, index) in movies" :key="index + movie.id">
              <h1>{{ movie.title }}</h1>
              <h2>{{ movie.original_title }}</h2>
              <h3>{{ movie.original_language }}</h3>
              <h4>{{ movie.vote_average }}</h4>
          </li>
      </ul>
      <!-- <button @click="consoleLog(movies)">clicca</button> -->
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
        // consoleLog(string) {
        //  console.log(string);
        //  if(this.movie) {
        //         this.moviesNew = this.movies.map(movie => ({ title: movie.title, original_title: movie.original_title, original_language: movie.original_language, vote_average:movie.vote_average }));
        //         return this.moviesNew
        //     } else {
        //         this.moviesNew = null;
        //         return this.moviesNew
        //     }
        // },
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