<template>
  <li>
      <div>
          <span v-if="!this.poster_path">unavailable</span>
          <img v-else :src="`${this.urlImg}${this.poster_sizes[2]}${this.poster_path}`" alt="ciao">
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
      <div>Voto medio: {{ vote_average }}</div>
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
    }
}
</script>

<style lang="scss" scoped>
@import '~mdb-ui-kit/css/mdb.min.css';

li {
    margin-top: 2em;
}
.red {
    color: red;
}
</style>