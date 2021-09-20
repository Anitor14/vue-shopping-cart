<template>
  <body>
    <Header title="SHOPPING CART" />
    <Section @addToCart="addToCart" :cards="cards" />
    <Checkout :updatedCards="updatedCards" />
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
      updatedCards: {},
    };
  },
  methods: {
    // This fetches the whole database
    async fetchCards() {
      const res = await fetch("http://localhost:3000/products");
      const data = await res.json();
      return data;
    },
    // This fetches just a single database of the inputed id.
    async fetchCard(id) {
      const res = await fetch(`http://localhost:3000/products/${id}`);
      const data = await res.json();

      return data;
    },
    async addToCart(id) {
      // if(status === false){
      //   alert("You have alread added this to the cart")
      //   return
      // }
      let itemToAddToCart = await this.fetchCard(id);
      console.log(itemToAddToCart);
      const updCards = { ...itemToAddToCart, status: !itemToAddToCart.status };
      console.log(updCards);

      const res = await fetch(`http://localhost:3000/products/${id}`, {
        method: "PUT",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(updCards),
      });

      const data = await res.json();

      this.updatedCards = this.cards.map((card) =>
        card.id === id ? { ...card, status: data.status } : card
      );
    },
  },
  async created() {
    this.cards = await this.fetchCards();
    this.updatedCards = await this.addToCart();
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
