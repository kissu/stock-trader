<template lang='pug'>
  .container
    app-header
    .row
      .col-xs-12
        router-view
</template>

<script>
  import Header from './components/Header.vue'

  export default {
    components: {
      appHeader: Header
    }
  }
</script>

<style>
  body {
    padding: 30px;
  }
</style>
