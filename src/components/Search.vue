<template>
   <div class="search">
     <h1>Questa sera voglio vedere:</h1>
    <input
      id="search"
      v-model="inputText"
      type="text"
      name="search"
      @keyup.enter="$emit('doSearch', inputText)"
    >
    <button
      class="btn-search"
      type="submit"
      @click="$emit('doSearch', inputText)"
    >
      GO!
    </button>
  </div>
</template>

<script>
export default {
    name:"Search",
    data() {
        return {
            inputText: "",
        }
    },
}
</script>

<style lang="scss" scoped>
.search {
  display: flex;
  justify-content: center;
  align-items: center;
  h1 {
    margin-right: 0.5em;
  }
  #search {
    padding: 1em;
    border: 5px solid rgb(255,241,1);
  }
  .btn-search {
    padding: 0 0.5em;
    margin-left: 1em;
    font-size: 2em;
    font-weight: 800;
    background-color: rgb(255,241,1);
    border-radius: 2em;
    box-shadow: 0px 0px 10px rgb(240,168,1);
  }
}
</style>