<template>
  <li>
      <div v-if="(this.title)">
        <div class="red">Titolo: {{ title }}</div>
        <div>Titolo originale: {{ original_title }}</div>
      </div>
      <div v-else class="red">Titolo: {{ original_name }}</div>
      <div>Lingua: <i :class="'flag flag-' + getFlag(original_language)"></i></div>
      <div>Voto medio: {{ vote_average }}</div>
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
        original_name: {
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

.red {
    color: red;
    margin-top: 2em;
}
</style>