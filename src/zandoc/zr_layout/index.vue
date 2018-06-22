<template>
  <div class="container">

    <div class="doc-title zr-hairline--bottom">LAYOUT</div>

    <div class="zr-panel-title">基础用法</div>
    <div class="doc-description">Layout 组件提供了24列栅格，添加 zr-col-x 可以设置元素所占宽度</div>
    <div class="zr-panel">
      <div class="zr-row">
        <div class="zr-col zr-col-8">
          span: 8
        </div>
        <div class="zr-col zr-col-8">
          span: 8
        </div>
        <div class="zr-col zr-col-8">
          span: 8
        </div>
      </div>
    </div>

    <div class="zr-panel-title">offset</div>
    <div class="doc-description">添加 zr-col-offset-x 类可以设置列的偏移宽度，计算方式与 span 相同</div>
    <div class="zr-panel">
      <div class="zr-row">
        <div class="zr-col zr-col-4">span: 4</div>
        <div class="zr-col zr-col-10 zr-col-offset-4">offset: 4, span: 10</div>
      </div>
      <div class="zr-row">
        <div class="zr-col zr-col-12 zr-col-offset-12">offset: 12, span: 12</div>
      </div>
    </div>

  </div>

</template>

<script>
  export default {
    data () {
      return {}
    }
  }
</script>
<style  scoped>
  .zr-col {
    line-height: 30px;
    text-align: center;
    background-color: #39a9ed;
    font-size: 12px;
    color: #fff;
  }

  .zr-col:nth-child(even) {
    background-color: #66c6f2;
  }
</style>
