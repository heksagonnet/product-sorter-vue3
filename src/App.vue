<script setup>
import { ref } from 'vue'
import ProductList from './components/ProductList.vue'

const products = ref([
  { title: 'Phone', colour: 'Grey', price: 549, id: 1 },
  { title: 'Mechanical Keyboard', colour: 'Blue', price: 79, id: 2 },
  { title: 'LCD Monitor', colour: 'Black', price: 127, id: 3 },
  { title: 'Desktop', colour: 'Red', price: 2132, id: 4 },
  { title: 'Laptop', colour: 'White', price: 1264, id: 5 },
])

const orderBy = ref('title')

const handleClick = (term) => {
  orderBy.value = term
}
</script>

<template>
  <h1 class="title">The Store</h1>
  <div class="orders">
    <button @click="handleClick('title')">Title</button>
    <button @click="handleClick('colour')">Colour</button>
    <button @click="handleClick('price')">Price</button>
  </div>
  <ProductList :products="products" :orderBy="orderBy" />
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Corinthia:wght@700&display=swap');
html {
  background-color: whitesmoke;
}
#app {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  max-width: 1000px;
  margin: 60px auto;
}
.orders {
  display: flex;
  justify-content: space-around;
  max-width: 70%;
  margin: 0 auto;
}
.orders button {
  margin: 10px;
  padding: 10px;
  cursor: pointer;
  font-weight: bold;
  border-radius: 10px;
  color: #2c3e50;
  background-color: rgb(255, 247, 203);
  box-shadow: lightslategray 0 1px 2px;
  border: none;
  transition: all ease 0.3s;
}
.orders button:hover {
  background-color: rgb(241, 237, 212);
}
.title {
  color: gold;
  text-shadow: 2px 2px #2c3e50;
  font-family: 'Corinthia', cursive;
  font-size: 100px;
  margin: 0;
}
</style>
