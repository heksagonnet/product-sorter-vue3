<script setup>
import { computed } from 'vue'

const props = defineProps({ products: Array, orderBy: String })

const orderedProducts = computed(() => {
  return [...props.products].sort((a, b) => {
    return a[props.orderBy] > b[props.orderBy] ? 1 : -1
  })
})
</script>

<template>
  <div>
    <p>Sort by: {{ orderBy }}</p>
    <div class="product-container">
      <transition-group name="sorter">
        <div
          class="product"
          v-for="product in orderedProducts"
          :key="product.id"
        >
          <h1>{{ product.title }}</h1>
          <p>{{ product.colour }}</p>
          <p>${{ product.price }}</p>
        </div>
      </transition-group>
    </div>
  </div>
</template>

<style>
.product-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
.product {
  height: 100%;
  width: 40%;
  padding: 10px 0;
  margin: 5px;
  box-shadow: lightslategray 0 1px 2px;
  border-radius: 10px;
  background-color: #fdfdfd;
}
.product h1 {
  font-size: large;
}
.sorter-move {
  transition: all 1s;
}
</style>
