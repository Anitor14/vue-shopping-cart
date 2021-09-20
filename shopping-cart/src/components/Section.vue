<template>
  <div class="section">
    <div :key="card.id" v-for="card in cards">
      <Card :card="card" @addToCart="$emit('addToCart',card.id,card.status)" />
    </div>
  </div>
</template>

<script>
import Card from "./Card";
export default {
  name: "Section",
  props: {
    cards: Array,
  },
  components: {
    Card,
  },
  emits:['addToCart']
};
</script>

<style scoped>
.section {
  padding-top: 50px;
  display: flex;
  margin: 10px;
  flex-wrap: wrap;
  justify-content: space-around;
  width: 100%;
  margin: auto;
}
</style>
