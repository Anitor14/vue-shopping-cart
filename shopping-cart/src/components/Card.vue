<template>
  <div class="card" style="width:18rem">
    <img
      :src="card.image"
      class="card-img-top"
    />
    <div class="card-body">
        <h5 class="card-title">{{card.name}}</h5>
        <p class="card-price">{{`₦${card.price}`}}</p>
        <a href="#" class="btn btn-primary btn-to-cart">Add to cart</a>
    </div>
  </div>
</template>

<script>
export default {
    name:"Card",
    props:{
        card:Object,
    }
}
</script>

<style scoped>
/* .card{
    margin: 15px;
    height: 200px;
} */
.card{
    margin: 15px;
}
.card-img-top{
    height: 100%;
    width: 100%;
    object-fit: cover;
}
</style>
