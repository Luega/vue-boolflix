<template>
  <main>
      <h1 v-if="!this.info">Scrivi nel campo di ricerca.</h1>
      <ul v-else-if="this.info.length != 0">  
        <Card 
        v-for="(card, index) in info"
        :key="index + card.id"
        :title="card.title"
        :name="card.name"
        :original_title="card.original_title"
        :original_name="card.original_name"
        :original_language="card.original_language"
        :vote_average="card.vote_average"
        :poster_path="card.poster_path"
        :id="card.id"
        />
      </ul>
      <h1 v-else>NON CI SONO RISULTATI DISPONIBILI</h1>
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
            info: null,
        }
    },
    props: {
        movieList: {
            type: Array,
        },
        tvList: {
            type: Array,
        },
    },
    methods: {
        
    },
    watch: {
        tvList: function (newArray) {
            this.info = newArray.concat(this.movieList);
            console.log(this.info);
        }
    }
}
</script>

<style lang="scss" scoped>

</style>