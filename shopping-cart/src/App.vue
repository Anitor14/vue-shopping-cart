<template>
  <body>
    <Header title="SHOPPING CART" />
    <Section @addToCart="addToCart" :cards="cards" />
    <Checkout :card="card" />
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
      card: {},
    };
  },
  methods: {
    async fetchCards() {
      const res = await fetch("http://localhost:3000/products");
      const data = await res.json();

      return data;
    },
    async addToCart(id) {
      const res = await fetch(`http://localhost:3000/products/${id}`);
      const data = await res.json();
      const newData = await this.newData(data);
      return newData;
      console.log(newData);
      // console.log(newData);

      // const postChange = await fetch(`http://localhost:3000/products/${id}`, {
      //   method: "PUT",
      //   headers: {
      //     "Content-type": "application/json",
      //   },
      //   body: JSON.stringify(newData),
      // });
      // console.log(postChange);
      // return postChange;
    },
    async newData(data) {
      const updCards = { ...data, status: !data.status };
      return updCards;
    },
  },
  async created() {
    this.cards = await this.fetchCards();
    this.card = await this.addToCart();
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
