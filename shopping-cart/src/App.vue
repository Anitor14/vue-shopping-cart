<template>
  <body>
    <Header title="SHOPPING CART" />
    <Section @addToCart="addToCart" :cards="cards" />
    <Checkout :cards="cards" @remove-card="removeCard" />
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
      cards: {},
      // updatedCards: {},
    };
  },
  methods: {
    // This fetches the whole database
    async fetchCards() {
      const res = await fetch("http://localhost:3000/products");
      // console.log(res);
      const data = await res.json();
      // this.addToCart(id,status);
      return data;
    },
    // This fetches just a single database of the inputed id.
    async fetchCard(id) {
      const res = await fetch(`http://localhost:3000/products/${id}`);
      const data = await res.json();

      return data;
    },
    async addToCart(id,status) {
      if(status === false){
        alert("You have alread added this to the cart");
        return
      }
      // if(id == undefined) return;
      // console.log(id);

      let itemToAddToCart = await this.fetchCard(id); // fetch the card with this id.
      console.log(itemToAddToCart);
      const updCards = { ...itemToAddToCart, status: !itemToAddToCart.status }; // reverse the value of the status of the card.
      console.log(updCards);

      //convert the value of this card in the database and fetch this database.
      const res = await fetch(`http://localhost:3000/products/${id}`, {
        method: "PUT",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(updCards),
      });

      let data = await res.json();
      console.log(data)
    },
    async removeCard(id) {
      console.log("this card has been removed");
      if(confirm('Are you sure you want to delete this item')){
        let itemToAddToCart = await this.fetchCard(id); // fetch the card with this id.
      console.log(itemToAddToCart);
      const updCards = { ...itemToAddToCart, status: !itemToAddToCart.status }; // reverse the value of the status of the card.
      console.log(updCards);

        const res = await fetch(`http://localhost:3000/products/${id}`, {
        method: "PUT",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(updCards),
      });
      }
    },
  },
  
  async created() {
    this.cards = await this.fetchCards();
  },
  async beforeUpdate(){
    this.cards = await this.fetchCards();
  },
  async updated(){
    this.cards = await this.fetchCards();
  }
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
