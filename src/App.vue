<template>
  <div id="app">
    <Header
    @inputTextToApp="fillInputText($event)"
    />
    <Main
    :inputText="this.inputText" 
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import Main from "./components/Main.vue"

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      inputText:"",
    };
  },
  methods: {
    fillInputText(value) {
      this.inputText = value;
    }
  }
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
