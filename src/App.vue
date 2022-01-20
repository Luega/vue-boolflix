<template>
  <div id="app">
    <Header
    @inputTextToApp="getMovies($event)"
    />
    <Main
    :movies="this.movies" 
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import Main from "./components/Main.vue"
import axios from "axios";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      movies: null,
      query: "https://api.themoviedb.org/3/search/",
      api_key:"72c83988e48ed668d3d11346217d3feb",
    };
  },
  methods: {
    getMovies(text) {
      const endpoint = "movie";
      const parameters = {
        api_key: this.api_key,
        language:"en-US",
        query: text,                                                       
      };
      axios.get(`${this.query}${endpoint}`, { params: parameters})
      .then((result) => {
        console.log(result);
        this.movies = result.data.results;
      }) 
      .catch((error) => {
        console.log(error);
      })
    }
  },
};
</script>

<style lang="scss" scoped>

</style>

// Milestone 2:
// Trasformiamo la stringa statica della lingua in una vera e propria bandiera della nazione corrispondente, gestendo il caso in cui non abbiamo la bandiera della nazione ritornata dall’API (le flag non ci sono in FontAwesome).

// Allarghiamo poi la ricerca anche alle serie tv. Con la stessa azione di ricerca dovremo prendere sia i film che corrispondono alla query, sia le serie tv, stando attenti ad avere alla fine dei valori simili (le serie e i film hanno campi nel JSON di risposta diversi, simili ma non sempre identici)
// Qui un esempio di chiamata per le serie tv:
// https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it_IT&query=scrubs

