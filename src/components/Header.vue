<template>
  <header class="header">
      <div class="logo-small">
          <img :src="this.logoSmall" alt="">
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
            logoSmall: "required(../logo.png)",
        };
    },
    methods: {
        sendToApp(value) {
            if (value != "") {
                this.$emit('inputTextToApp', value);
            }
        },
  }
}
</script>

<style lang="scss" scoped>
.header {
    width: 100%;
    height: 100px;
    background-color: red;
    display: flex;
    justify-content: center;
    align-items: center;

}
</style>