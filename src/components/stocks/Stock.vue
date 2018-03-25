<template lang="pug">
  .col-xs-6.col-md-4
    .panel.panel-primary
      .panel-heading
        h3.panel-title NAME
          small Price:
      .panel-body
        .pull-left
          input(type='number' class='form-control' placeholder='Quantity')
        .pull-right
          button(class='btn btn-danger') Buy
</template>
