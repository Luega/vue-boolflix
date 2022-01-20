<template>
  <header>
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

</style>