<template>
  <header class="header">
      <div class="logo-small">
          <img src= "../assets/img/free-movie-time.png" alt="">
      </div>
      <Search
      @doSearch="sendToApp($event)"
      />
  </header>
</template>

<script>
import Search from "./Search.vue";

export default {
    name:"Header",
    components: {
        Search,
    },
    data() {
        return {
        };
    },
    methods: {
        sendToApp(value) {
            this.$emit('inputTextToApp', value);
        },
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/partials/_variables.scss";

.header {
    width: 100%;
    padding: 2em 0 0 0;
    background-color: $firstColor;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    .logo-small {
        margin-bottom:4em;
        img {
            widows: 100%;
            height: 100%;
            object-fit: contain;
        }
    }
}
</style>