<template>
  <div>
    <h4>🛒 Cart</h4>
    <ul class="list-group">
      <li v-for="(item, index) in cart" :key="index" class="list-group-item d-flex justify-content-between">
        {{ item.name }} - ${{ item.price }}
        <button class="btn btn-sm btn-danger" @click="$emit('remove-from-cart', index)">X</button>
      </li>
    </ul>
    <p class="mt-2">Total: ${{ totalPrice }}</p>
  </div>
</template>

<script>
export default {
  props: {
    cart: Array,
    totalPrice: Number
  }
}
</script>
