<template>
    <div class="cart-row" v-if="card.status === false">
        <div class="cart-item cart-column">
            <img :src="card.image" class="cart-item-image">
            <span class="cart-item-title">{{card.name}}</span>
        </div>
        <span class="cart-price cart-column">{{`₦${card.price}`}}</span>   
        <div class="cart-quantity cart-column">
            <input type="number" class="cart-quantity-input" v-model="amount" @change="change" >
            <button class="btn btn-danger" type="button" @click ="$emit('remove-card',card.id)">Remove</button>
        </div>
    </div>
</template>

<script>
export default {
    name:"CartRow",
    data(){
      return{
        amount:1,
      }
    },
    props:{
        card:Object,
    },
    methods:{
      convertToInteger(string){
        return parseInt(string);
      },
      change(){
        console.log(this.amount);
        if(this.amount < 1){
          this.amount=0;
        }
      }
    },
}
</script>
<style scoped>
.section-header{
    display: flex;
    text-align: center;
    justify-content: space-around;
    /* margin: 10px auto; */
    padding-top: 10px;
}
.cart-header {
  font-weight: bold;
  font-size: 1.25rem;
  color: #333;
}
.cart-column {
  display: flex;
  align-items: center;
  border-bottom: 1px solid black;
  margin-right: 1.5em;
  padding-bottom: 10px;
  margin-top: 10px;
}
.cart-row {
  display: flex;
}
.cart-item {
  width: 45%;
}
.cart-price {
  width: 20%;
  font-size: 1.2em;
  color: #333;
}
.cart-quantity {
  width: 35%;
}
.cart-item-title {
  color: #333;
  margin-left: 0.5em;
  font-size: 1.2em;
}
.cart-item-image {
  width: 75px;
  height: auto;
  border-radius: 10px;
}
.btn-danger {
  color: white;
  background-color: #eb5757;
  border: none;
  border-radius: 0.3em;
  font-weight: bold;
}
.btn-danger:hover {
  background-color: #cc4c4c;
}
.cart-quantity-input {
  height: 34px;
  width: 50px;
  border-radius: 5px;
  border: 1px solid #56ccf2;
  background-color: #eee;
  color: #333;
  padding: 0;
  text-align: center;
  font-size: 1.2em;
  margin-right: 25px;
}
.cart-row:last-child {
  border-bottom: 1px solid black;
}
.cart-row:last-child .cart-column {
  border: none;
}
.cart-total {
  text-align: end;
  margin-top: 10px;
  margin-right: 10px;
}
.cart-total-title {
    font-weight: bold;
    font-size: 1.5em;
    color: black;
    margin-right: 20px;
}
.cart-total-price {
    color: #333;
    font-size: 1.1em;
}
.btn-purchase {
    display: block;
    margin: 40px auto 80px auto;
    font-size: 1.75em;
}
</style>