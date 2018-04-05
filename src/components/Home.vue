<template lang='pug'>
  div
    h1 Trade or View your portfolio
    h6 Save & Load Data
    h6 End of the day
    hr
    p Your funds: {{ funds }}
</template>

<script>
  export default {
    computed: {
      funds() {
        return this.$store.getters.funds
      }
    }
  }
</script>
