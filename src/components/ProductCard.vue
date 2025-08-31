<template>
  <div class="card p-3">
    <img :src="product.image" class="card-img-top" alt="product" />
    <div class="card-body">
      <h5 class="card-title">{{ product.name }}</h5>
      <p>{{ product.description }}</p>
      <p class="fw-bold">${{ product.price }}</p>

      <!-- Stock Status -->
      <p 
        v-if="product.inStock === true" 
        class="in-stock">
        In Stock
      </p>
      <p 
        v-else-if="product.inStock === 'limited'" 
        class="limited-stock">
        Limited Stock
      </p>
      <p 
        v-else 
        class="out-of-stock">
        Out of Stock
      </p>

      <!-- Add to Cart -->
      <button 
        class="btn btn-primary" 
        :disabled="product.inStock === false" 
        @click="$emit('add-to-cart', product)">
        Add to Cart
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    product: Object
  }
}
</script>

<style scoped>
.out-of-stock { color: grey; }
.in-stock { color: green; }
.limited-stock { color: orange; }
</style>
