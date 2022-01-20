<template>
  <main>
      <ul>  
        <Card 
        v-for="(card, index) in info"
        :key="index + card.id"
        :title="card.title"
        :original_title="card.original_title"
        :original_language="card.original_language"
        :vote_average="card.vote_average"
        :id="card.id"
        />
      </ul>
  </main>
</template>

<script>
import Card from "./Card.vue";

export default {
    name:"Main",
    components: {
        Card,
    },
    data() {
        return {
        }
    },
    props: {
        info: {
            type: Array,
        }
    },
    methods: {
     
    },
    
}
</script>

<style lang="scss" scoped>

</style>