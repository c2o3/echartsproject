<template>
  <div class="item">
    <slot></slot>
  </div>
</template>

<script setup>
</script>

<style scoped lang='scss'>
    .item{
        height: 5.125rem;
        border: 1px blue solid;
        margin: .25rem;
        background-color: rgba(12,130,255,.85);
    }
</style>