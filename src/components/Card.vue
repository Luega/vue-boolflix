<template>
  <li class="info-card">
      <img class="poster" :src="this.poster_path ? `${this.urlImg}${this.poster_sizes[3]}${this.poster_path}` : this.unavailableImg" alt="ciao">
      <div class="info">
        <div class="red" v-if="(this.title)">Titolo: {{ title }}</div>
        <div class="red" v-else>Titolo: {{ name }}</div>
        <div v-if="(this.original_title)">Titolo originale: {{ original_title }}</div>
        <div v-else>Titolo originale: {{ original_name }}</div>
        <div>
            Lingua:
            <span 
                v-if="
                this.original_language == 'xx' || 
                this.original_language == 'ja' ||
                this.original_language == 'ko' ||
                this.original_language == 'da' ||
                this.original_language == 'zh' ||
                this.original_language == 'ur' ||
                this.original_language == 'hi'
                "
                >unavailable
            </span> 
            <i v-else :class="'flag flag-' + getFlag(original_language)"></i>
        </div>
        <font-awesome-icon class="yellow-star" v-for="(star, indice) in this.newVote" :key="'a-' + indice" :icon="['fas','star']"/>
        <font-awesome-icon v-for="(emptyStar, index) in this.emptyStars" :key="'b-' + index" :icon="['fas','star']"/>
      </div>
  </li>
</template>

<script>
export default {
    name: "card",
    data() {
        return {
            urlImg: "https://image.tmdb.org/t/p/",
            poster_sizes: [
            "w92",
            "w154",
            "w185",
            "w342",
            "w500",
            "w780",
            "original"
            ],
            unavailableImg: "https://www.associazionejam.it/wp-content/uploads/2017/04/non-disponibile-300x300.png",
        }
    },
    props: {
        title: {
            type: String,
        },
        name: {
            type: String,
        },
        original_title: {
            type: String,
        },
        original_name: {
            type: String,
        },
        original_language: {
            type: String,
        },
        vote_average: {
            type: Number,
        },
        poster_path: {
            type: String,
        },
        id: {
            type: Number,
        }
    },
    methods: {
        getFlag(lang) {
            if (lang === 'en') {
            return 'us';
            }
            return lang;
        },
    },
    computed: {
        newVote: function () {
            return Math.ceil(this.vote_average / 2)
        },
        emptyStars: function () {
            return 5 - this.newVote
        }
    },
}
</script>

<style lang="scss" scoped>
@import "../assets/partials/_variables.scss";
@import "~mdb-ui-kit/css/mdb.min.css";

.info-card { 
    background-color: chocolate;
    border-radius: 1em;
    flex-basis: calc(100% / 6);
    overflow: hidden;
    .poster {
        width: 100%;
        height: 100%;
    }
    .info {
        display: none;
    }
}
li {
    margin-top: 2em;
}
.red {
    color: red;
}
img {
    width: 185px;
    height: auto;
}
.yellow-star {
    color: rgb(255, 214, 51);
}
</style>