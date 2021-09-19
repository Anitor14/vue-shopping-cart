<template>
  <body>
    <Header title="SHOPPING CART" />
    <Section :cards="cards"/>
    <Checkout />
    <Footer />
  </body>
</template>

<script>
import Header from "./components/Header";
import Section from "./components/Section";
import Checkout from "./components/Checkout";
import Footer from "./components/Footer";

export default {
  name: "App",
  components: {
    Header,
    Section,
    Checkout,
    Footer,
  },
  data() {
    return {
      cards: [],
    };
  },
  methods: {
    async fetchCards() {
      const res = await fetch("http://localhost:3000/products");
      const data = await res.json();

      return data;
    },
  },
  async created() {
    this.cards = await this.fetchCards();
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Raleway:300,400,700");
@import url("https://fonts.googleapis.com/css?family=Metal+Mania");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  background-color: white;
  width: 100%;
}
</style>
