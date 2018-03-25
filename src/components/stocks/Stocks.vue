<template lang="pug">
  div
    app-stock(v-for="stock in stocks" :stock="stock")
</template>

<script>
  import Stock from './Stock.vue'

  export default {
  data() {
    return {
      stocks: [
        { id: 1, name: 'Ferrari', price: 50},
        { id: 2, name: 'Lamborgini', price: 100},
        { id: 3, name: 'Audi', price: 150},
        { id: 4, name: 'Lotus', price: 200},
      ]
    }
  },
  components: {
    appStock: Stock
  }
}
</script>
