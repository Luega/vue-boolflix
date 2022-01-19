<template>
  <div>
      <h1>{{ title }}</h1>
      <h2>{{ original_title }}</h2>
      <h3>{{ original_language }}</h3>
      <h4>{{ vote_average }}</h4>
  </div>
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
            type: String,
        }
    }
}
</script>

<style lang="scss" scoped>

</style>