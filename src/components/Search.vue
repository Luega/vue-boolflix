<template>
   <div class="search">
    <input
      id="search"
      v-model="inputText"
      type="text"
      name="search"
      @keyup.enter="$emit('doSearch', inputText)"
    >
    <button
      type="submit"
      @click="$emit('doSearch', inputText)"
    >
      Cerca
    </button>
  </div>
</template>

<script>
export default {
    name:"Search",
    data() {
        return {
            inputText: "null",
        }
    },
}
</script>

<style lang="scss" scoped>

</style>