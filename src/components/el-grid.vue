<template>
  <div class="el-grid">
    <slot />
  </div>
</template>

<script>
export default {
  name: 'el-grid'
}
</script>

<style lang="scss">
.el-grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-template-rows: auto;
  grid-gap: 20px;
}
</style>
