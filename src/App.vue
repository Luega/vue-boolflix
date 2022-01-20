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

// Milestone 1:
// Creare un layout base con una searchbar (una input e un button) in cui possiamo scrivere completamente o parzialmente il nome di un film. Possiamo, cliccando il  bottone, cercare sull’API tutti i film che contengono ciò che ha scritto l’utente.

// Vogliamo dopo la risposta dell’API visualizzare a schermo i seguenti valori per ogni film trovato: 
// Titolo
// Titolo Originale
// Lingua
// Voto
