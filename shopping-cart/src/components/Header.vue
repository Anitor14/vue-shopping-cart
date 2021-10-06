<template>
  <header>
    <div class="branding">
      <h3 class="branding-name">{{ title }}</h3>
    </div>
    <div class="opening-pic"></div>
  </header>
</template>

<script>
export default {
  name: "Header",
  props: {
    title: String,
  },
  components: {},
};
</script>

<style scoped>
.branding {
  min-height: 90px;
  text-align: center;
  vertical-align: center;
  font-family: "Metal Mania";
  color: white;
  background: rgb(67, 67, 246);
  border-bottom: 2px solid black;
  background-size: cover;
  background-position-y: 50%;
  background-repeat: no-repeat;
  color: rgb(255, 255, 255);
  background-image: url(../assets/images/header-image-1-1799x1012.jpg);
  padding-top: 20px;
  border-bottom: 2px solid black;
  font-size: 20px;
}
.opening-pic {
  min-height: 120px;
  background-image: url(../assets/images/freestocks-_3Q3tsJ01nc-unsplash.jpg);
  background-size: cover;
  background-repeat: no-repeat;
  background-position: 50%;
}
</style>
