<template>
  <label for="max-price" class="form-label h2"
    >Max Price (${{ modelValue }})</label
  >
  <div class="badge bg-success ml-3">results: {{ products.length }}</div>

  <input
    type="range"
    class="form-range"
    min="0"
    max="130"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>
<script>
export default {
  props: ['products', 'modelValue']
}
</script>
