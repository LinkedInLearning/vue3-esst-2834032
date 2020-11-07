<template>
  <div class="container">
    <h1>Checkout</h1>

    <table class="table table-hover">
      <caption class="text-right h3">
        <b>Total:</b>
        Total
      </caption>
      <thead>
        <tr>
          <th scope="col"></th>
          <th scope="col">Item</th>
          <th scope="col" class="text-center">Qty</th>
          <th scope="col" class="text-right">Price</th>
          <th scope="col" class="text-right">Sub-total</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td class="text-center">
            <div class="btn-group" role="group" aria-label="Basic example">
              <button class="btn btn-success">
                +
              </button>
              <button class="btn btn-outline-success">
                -
              </button>
            </div>
          </td>
          <th scope="row">item name</th>
          <td class="text-center">item qty</td>
          <td class="text-right">
            price
          </td>
          <td class="text-right">
            subtotal
          </td>
        </tr>
      </tbody>
    </table>
    <router-link class="btn btn-sm btn-success" to="/"
      >Keep Shopping</router-link
    >
  </div></template
>

<script>
export default {}
</script>

<style></style>
