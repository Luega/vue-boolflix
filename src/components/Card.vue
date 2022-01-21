<template>
  <li>
      <div>
          <img :src="this.poster_path ? `${this.urlImg}${this.poster_sizes[2]}${this.poster_path}` : this.unavailableImg" alt="ciao">
      </div>
      <div v-if="(this.title)">
        <div class="red">Titolo: {{ title }}</div>
        <div>Titolo originale: {{ original_title }}</div>
      </div>
      <div v-else class="red">Titolo: {{ original_name }}</div>
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
      <font-awesome-icon class="yellow-star" v-for="(star, indice) in this.newVote" :key="indice" :icon="['fas','star']"/>
      <font-awesome-icon v-for="(emptyStar, index) in this.emptyStars" :key="index" :icon="['fas','star']"/>
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

@import "~mdb-ui-kit/css/mdb.min.css";

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