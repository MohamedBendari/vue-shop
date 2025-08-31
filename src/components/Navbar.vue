<template>
  <nav class="navbar navbar-dark bg-dark px-3">
    <a class="navbar-brand">Vue Store</a>
    <span class="badge bg-success">Cart: {{ cartCount }}</span>
  </nav>
</template>

<script>
export default {
  props: {
    cartCount: Number
  }
}
</script>
