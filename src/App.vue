<template>
  <div>
    <Navbar :cartCount="cartCount" />

    <div class="container mt-4">
      <h1 class="text-center mb-4">Vue Store 🛍</h1>

      <!-- Discount -->
      <div v-if="discount > 0" class="alert alert-info">
        🎉 Discount available: {{ discount }}%
      </div>

      <!-- Toggle Products -->
      <button class="btn btn-secondary mb-3" @click="showProducts = !showProducts">
        Toggle Products
      </button>

      <!-- Products -->
      <div v-show="showProducts">
        <div class="row">
          <div class="col-md-4 mb-3" v-for="product in products" :key="product.id">
            <ProductCard :product="product" @add-to-cart="addToCart" />
          </div>
        </div>
      </div>

      <!-- No products -->
      <p v-if="products.length === 0">No products available</p>

      <!-- Cart -->
      <Cart 
        v-if="cart.length > 0" 
        :cart="cart" 
        :totalPrice="totalPrice" 
        @remove-from-cart="removeFromCart" 
      />
    </div>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import ProductCard from './components/ProductCard.vue'
import Cart from './components/Cart.vue'

export default {
  components: { Navbar, ProductCard, Cart },
  data() {
    return {
      products: [
  {
    id: 1,
    name: "Laptop",
    price: 1200,
    inStock: true,
    description: "Powerful laptop for developers",
    image: "https://images.unsplash.com/photo-1517336714731-489689fd1ca8?w=400"
  },
  {
    id: 2,
    name: "Phone",
    price: 800,
    inStock: false,
    description: "Latest smartphone",
    image: "https://images.unsplash.com/photo-1511707171634-5f897ff02aa9?w=400"
  },
  {
    id: 3,
    name: "Headphones",
    price: 150,
    inStock: "limited",
    description: "Noise cancelling",
    image: "https://images.unsplash.com/photo-1511367461989-f85a21fda167?w=400"
  }
],

      cart: [],
      cartCount: 0,
      showProducts: true,
      discount: 10
    }
  },
  methods: {
    addToCart(product) {
      this.cart.push(product)
      this.cartCount++
      alert(`${product.name} added to cart!`)
    },
    removeFromCart(index) {
      this.cart.splice(index, 1)
      this.cartCount--
    }
  },
  computed: {
    totalPrice() {
      return this.cart.reduce((sum, p) => sum + p.price, 0)
    }
  }
}
</script>
