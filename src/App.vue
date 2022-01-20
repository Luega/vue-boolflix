<template>
  <div id="app">
    <Header
    @inputTextToApp="searchInfo($event)"
    />
    <Main
    :movieList="this.movieList" 
    :tvList="this.tvList" 
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
      inputText: "",
      query: "https://api.themoviedb.org/3/search/",
      api_key:"72c83988e48ed668d3d11346217d3feb",
      movieList: null,
      tvList: null,
    };
  },
  methods: {
    searchInfo(text){
      this.inputText = text;
      this.getMovies(this.inputText);
    },
    getMovies() {
      const endpoint = "movie";
      const parameters = {
        api_key: this.api_key,
        language:"en-US",
        query: this.inputText,                                                     
      };
      axios.get(`${this.query}${endpoint}`, { params: parameters})
      .then((result) => {
        this.movieList = result.data.results;
        console.log(this.movieList);
      }) 
      .catch((error) => {
        console.log(error);
      })
    },
    getTv() {
      const endpoint = "tv";
      const parameters = {
        api_key: this.api_key,
        language:"en-US",
        query: this.inputText,                                                     
      };
      axios.get(`${this.query}${endpoint}`, { params: parameters})
      .then((result) => {
        this.tvList = result.data.results;
        console.log(this.tvList);
      }) 
      .catch((error) => {
        console.log(error);
      })
    },
  },
  watch: {
    movieList: function() {
      this.getTv(this.inputText);
    }
  }
};
</script>

<style lang="scss" scoped>

</style>

// Milestone 2:
// Trasformiamo la stringa statica della lingua in una vera e propria bandiera della nazione corrispondente, gestendo il caso in cui non abbiamo la bandiera della nazione ritornata dall’API (le flag non ci sono in FontAwesome).


