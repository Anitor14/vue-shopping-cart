<template>
  <body>
    <Header title="SHOPPING CART" />
    <Section />
    <Checkout />
    <Footer />
  </body>
</template>

<script>
import Header from "./components/Header";
import Section from "./components/Section";
import Checkout from "./components/Checkout"
import Footer from "./components/Footer"

export default {
  name: "App",
  components: {
    Header,
    Section,
    Checkout,
    Footer
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Raleway:300,400,700');
@import url("https://fonts.googleapis.com/css?family=Metal+Mania");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica , sans-serif;
  background-color: white;
  width: 100%;
}
</style>
