<template>
    <div class="section">
        <Card />
    </div>
</template>

<script>
import Card from "./Card"
export default {
    name:'Section',
    components:{
        Card,
    }
}
</script>

<style scoped>
.section{
    padding-top: 50px;
    display: flex;
    margin: 10px;
    flex-wrap: wrap;
    justify-content: space-around;
    width: 100%;
    margin: auto;
    background-position: center;
    background-size: cover;
    background-position-y: 50%;
    background-position-y: 50%;
    background-color: white;
}
</style>