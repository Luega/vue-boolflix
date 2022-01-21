<template>
  <main class="main">
      <div class="container">
            <h1 class="write-in-input-script" v-if="!this.info">Scrivi nel campo di ricerca.</h1>
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
                :overview="card.overview"
                :id="card.id"
                />
            </ul>
            <h1 class="no-datas-script" v-else>NON CI SONO RISULTATI DISPONIBILI</h1>
      </div>
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
@import "../assets/partials/_variables.scss";

.main {
    width: 100%;
    min-height: calc(100vh - 413.6px);
    background-color: $secondColor;
    display: flex;
    justify-content: center;
    .container {
        width: 80%;
        padding: 2em;
        margin: 2em auto;
        background-color: $firstColor;
        border-radius: 5em;
        display: flex;
        ul {
            list-style: none;
            padding: 0;
            display: flex;
            flex-wrap: wrap;
        }
        .write-in-input-script,
        .no-datas-script {
            width: 100%;
            text-align: center;
        }
    }

}
</style>