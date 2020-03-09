<template>
  <div class="el-grid-item">
    <slot />
  </div>
</template>

<script>
export default {
  name: 'el-grid-item'
}
</script>

<style lang="scss">
.el-grid-item {
  min-width: 230px;
  border-radius: 4px;
  padding: 15px;
  border: 1px solid #000;
}
</style>
