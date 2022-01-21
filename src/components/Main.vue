<template>
  <main class="main">
      <div class="container">
            <div v-if="!this.info">
                <img class="img-question" src="../assets/img/question.jpg" alt="blue-eyes">
            </div>
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
            <div class="no-data-script-box" v-else>
                <h1>Non ci sono titoli correlati.</h1>
                <h2>Prova a scriverne un altro.</h2>
                <img class="img-no-data" src="../assets/img/no-data.find.jpg" alt="no-data-find">
            </div>
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
    min-height: calc(100vh - 465.6px);
    background-color: $secondColor;
    display: flex;
    justify-content: center;
    .container {
        width: 80%;
        padding: 2em;
        margin: 2em auto;
        background-color: $firstColor;
        border-radius: 0.5em;
        display: flex;
        ul {
            list-style: none;
            padding: 0;
            display: flex;
            flex-wrap: wrap;
        }
        img {
            border-radius: 1em;
        }
        .img-question {
            width: 100%;
            object-fit: contain;
        }
        .img-no-da {
            margin-top: 1em;
        }
        .write-in-input-script,
        .no-data-script-box {
            width: 100%;
            text-align: center;
        }
    }

}
</style>