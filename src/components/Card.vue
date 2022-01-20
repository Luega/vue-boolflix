<template>
  <li>
      <h1>Titolo: {{ title }}</h1>
      <h2>Titolo originale: {{ original_title }}</h2>
      <h3>Lingua: <i :class="'flag flag-' + getFlag(original_language)"></i></h3>
      <h4>Voto medio: {{ vote_average }}</h4>
  </li>
</template>

<script>
export default {
    name: "card",
    props: {
        title: {
            type: String,
        },
        original_title: {
            type: String,
        },
        original_language: {
            type: String,
        },
        vote_average: {
            type: Number,
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

h1 {
    color: red;
}
</style>