<template>
  <div class="home">
    <el-grid>
      <el-grid-item>This is one of grid items</el-grid-item>
      <el-grid-item>This is one of grid items</el-grid-item>
      <el-grid-item>This is one of grid items</el-grid-item>
      <el-grid-item>This is one of grid items</el-grid-item>
    </el-grid>
  </div>
</template>

<script>
import ElGrid from '@/components/el-grid'
import ElGridItem from '@/components/el-grid-item'
export default {
  name: 'Home',
  components: {
    ElGrid,
    ElGridItem
  }
}
</script>
