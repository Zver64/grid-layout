<template>
  <div class="el-grid">
    <slot />
  </div>
</template>

<script>
export default {
  name: 'el-grid',
  props: {
    filter: {
      default() {
        return []
      },
      type: Array
    }
  },
  watch: {
    filter(prop) {
      this.$children.forEach(item => {
        let visible = item.$props.tags.some(val => {
          return prop.includes(val)
        })
        if (visible) {
          item.$el.classList.remove('el-grid-item_hidden')
        } else {
          item.$el.classList.add('el-grid-item_hidden')
        }
      })
    }
  },
  mounted() {}
}
</script>

<style lang="scss">
.el-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  grid-template-rows: auto;
  grid-gap: 20px;
  grid-auto-flow: dense;
}
</style>
