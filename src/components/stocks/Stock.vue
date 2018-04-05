<template lang="pug">
  .col-xs-6.col-md-4
    .panel.panel-primary
      .panel-heading
        h3.panel-title {{ stock.name }}
          small  ({{ stock.price }})
      .panel-body
        .pull-left
          input(type='number' class='form-control' placeholder='Quantity' v-model="quantity")
        .pull-right
          button(class='btn btn-danger'
            @click='buyStock'
            :disabled="insufficientFunds || quantity < 1") {{ insufficientFunds ? '$$$' : 'Buy' }}
</template>

<script>
export default {
  props: ['stock'],
  data() {
    return {
      quantity: 0
    }
  },
  computed: {
    funds() {
      return this.$store.getters.funds
    },
    insufficientFunds() {
      return this.quantity * this.stock.price > this.funds
    }
  },
  methods: {
    buyStock() {
      const order = {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: this.quantity,
      }
      this.$store.dispatch('buyStock', order)
      this.quantity = 0
    }
  }
}
</script>
