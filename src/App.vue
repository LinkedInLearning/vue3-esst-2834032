<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/checkout">Checkout</router-link>
  </div>
  <div class="container">
    <router-view />
  </div>
</template>

<style lang="scss">
$primary: #6f42c1;
@import 'node_modules/bootstrap/scss/bootstrap';

  .dropdown-clip {
    overflow: hidden;
  }

  .dropdown-enter-active,
  .dropdown-leave-active {
    transition: all .5s ease-in-out;
    transform: auto;
  }

  .dropdown-enter-from, 
  .dropdown-leave-to {
    opacity: 0;
    transform:translateY(-300px);
  }

  .products-enter-active,
  .products-leave-active {
    transition: all .5s ease-in-out;
  }

  .products-enter-from {
    opacity: 0;
    transform:translateX(300px);
  }
  
  .products-leave-to {
    opacity: 0;
    transform:translateX(-300px);
  }

</style>
