<template>
  <div>
    <block v-if="nomore">
      <div class="zr-loadmore zr-loadmore--nomore">
        <div class="zr-loadmore__tips">
          <div class="zr-loadmore__dot"></div>
        </div>
      </div>
    </block>

    <block v-else-if="nodata">
      <div class="zr-loadmore zr-loadmore--nodata">
        <div class="zr-loadmore__tips">{{ nodata_str || '暂无数据' }}</div>
      </div>
    </block>

    <block v-else-if="loading">
      <div class="zr-loadmore">
        <div class="zr-loading"></div>
        <div class="zr-loadmore__tips">加载中...</div>
      </div>
    </block>
  </div>
</template>

<script>
  export default {
    props: ['nomore', 'nodata', 'loading']
  }
</script>

<style scoped>
</style>
