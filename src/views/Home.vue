<template>
  <section class="container">
    <label for="max-price" class="form-label h2">Max Price (${{ max }})</label>
    <div class="badge bg-success ml-3">
      results: {{ filteredProducts.length }}
    </div>

    <input
      v-model.number="max"
      type="range"
      class="form-range"
      min="0"
      max="130"
    />

    <transition-group name="products" appear>
      <div
        v-for="item in filteredProducts"
        :key="item.id"
        id="item-list"
        class="row align-items-center"
      >
        <product :item="item"></product>
      </div>
    </transition-group>
  </section>
</template>

<script>
import Product from '@/components/Product'

export default {
  name: 'Home',
  data: function() {
    return {
      max: 50,
      cart: [],
      displayCart: false,
      products: []
    }
  },
  components: {
    Product
  },
  created() {
    fetch('https://hplussport.com/api/products/order/price')
      .then(response => response.json())
      .then(data => {
        this.products = data
      })
  },
  computed: {
    filteredProducts() {
      return this.products.filter(item => item.price < this.max)
    }
  }
}
</script>
