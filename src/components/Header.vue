<template lang='pug'>
  nav(class='navbar navbar-default')
    div(class='container-fluid')
      div(class='navbar-header')
        router-link(to='/' class='navbar-brand') Stock Trader

      div(class='collapse navbar-collapse')
        ul(class='nav navbar-nav')
          router-link(to='/portfolio' activeClass='active' tag='li')
            a Portfolio
          router-link(to='/stocks' activeClass='active' tag='li')
            a Stocks
          li
            a(href='#') Link

        strong(class='navbar-text navbar-right') Funds: {{ funds | currency }}
        ul(class='nav navbar-nav navbar-right')
          li
            a(href="#" @click="endDay") End Day
          li(class="dropdown" :class="{open: isDropdownOpen}" @click="isDropdownOpen = !isDropdownOpen")
            a(href='#'
              class="dropdown-toggle"
              data-toggle="dropdown"
              role="button"
              aria-haspopup="true"
              aria-expanded="false") Save & Load
              span(class='caret')

            ul(class='dropdown-menu')
              li
                a(href='#' @click="saveData") Save Data
              li
                a(href='#' @click="loadData") Load Data

</template>

<script>
  import { mapActions } from 'vuex'

  export default {
    data() {
      return {
        isDropdownOpen: false
      }
    },
    computed: {
      funds() {
        return this.$store.getters.funds
      }
    },
    methods: {
      ...mapActions({
        randomizeStocks: 'randomizeStocks',
        fetchData: 'loadData'
      }),
      endDay() {
        this.randomizeStocks()
      },
      saveData() {
        const data = {
          funds: this.$store.getters.funds,
          stockPortfolio: this.$store.getters.stockPortfolio,
          stocks: this.$store.getters.stocks
        }
        this.$http.put('data.json', data)
      },
      loadData() {
        this.fetchData()
      }
    }
  }
</script>
