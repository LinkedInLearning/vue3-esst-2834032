<template>
  <nav class="navbar navbar-light sticky-top mr-3">
    <div
      v-if="cart.length"
      class=" w-100 navbar-text ml-auto d-flex justify-content-end position-relative"
    >
      <div
        class="mr-auto d-flex align-items-end flex-column bd-highlight mb-3 position-absolute"
      >
        <div class="mb-2">
          <span class="font-weight-bold bg-white"
            ><curr :amt="cartTotal"></curr
          ></span>
          <button
            @click="displayCart = !displayCart"
            class="btn btn-sm btn-success ml-3"
            id="cartDropdown"
            aria-haspopup="true"
            aria-expanded="false"
          >
            <fa icon="shopping-cart" />
            {{ cart.length }}
          </button>
        </div>
        <div class="dropdown-clip">
          <transition name="dropdown">
            <div
              v-if="displayCart"
              class="list-group"
              aria-labelledby="cartDropdown"
            >
              <div
                v-for="(item, index) in cart"
                :key="index"
                class="list-group-item d-flex justify-content-between"
              >
                <div>{{ item.name }}</div>
                <div class="ml-3 font-weight-bold">
                  <curr :amt="item.price"></curr>
                </div>
              </div>
            </div>
          </transition>
        </div>
      </div>
    </div>
  </nav>

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

    <custom-alert type="danger" close="true" v-if="cartTotal > 100">
    </custom-alert>

    <transition-group name="products" appear>
      <div
        v-for="item in filteredProducts"
        :key="item.id"
        id="item-list"
        class="row align-items-center"
      >
        <product :item="item" @add-to-cart="addToCart"></product>
      </div>
    </transition-group>
  </section>
</template>

<script>
import Curr from '@/components/Curr'
import CustomAlert from '@/components/CustomAlert'
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
    Curr,
    CustomAlert,
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
    },
    cartTotal() {
      return this.cart.reduce((inc, item) => Number(item.price) + inc, 0)
    }
  },
  methods: {
    addToCart(product) {
      this.cart.push(product)
      if (this.cartTotal >= 100) {
        this.salesBtn = 'btn-danger'
      }
    }
  }
}
</script>
