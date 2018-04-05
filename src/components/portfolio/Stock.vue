<template lang="pug">
  .col-xs-6.col-md-4
    .panel.panel-primary
      .panel-heading
        h3.panel-title {{ stock.name }}
          small  ({{ stock.price }} | Quantity: {{ stock.quantity }})
      .panel-body
        .pull-left
          input(type='number' class='form-control' placeholder='Quantity' v-model="quantity")
        .pull-right
          button(class='btn btn-danger'
            @click='sellStock'
            :disabled='quantity < 1') Sell
</template>

<script>
  import { mapActions } from 'vuex'

  export default {
    props: ['stock'],
    data() {
      return {
        quantity: 0
      }
    },
    methods: {
      ...mapActions([
        'sellStock'
      ]),
      sellStock() {
        const order = {
          stockId: this.stock.id,
          stockPrice: this.stock.price,
          quantity: this.quantity,
        }
        this.sellStock()
      }
    }
  }
</script>
