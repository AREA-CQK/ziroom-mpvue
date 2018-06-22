<template>
<div class="container">

  <div class="doc-title zr-hairline--bottom">BUTTON</div>

  <div class="zr-panel-title">普通按钮</div>
  <div class="zr-panel">
    <div class="zr-btns">
      <button class="zr-btn">取消订单</button>
      <button class="zr-btn zr-btn--primary">确认付款</button>
      <button class="zr-btn zr-btn--danger">确认付款</button>
      <button class="zr-btn zr-btn--warn">确认付款</button>
    </div>
  </div>

  <div class="zr-panel-title">大号按钮，没有边框线及圆角</div>
  <div class="zr-panel">
    <button class="zr-btn zr-btn--large zr-btn--primary">确认付款</button>
    <button class="zr-btn zr-btn--large zr-btn--warn">立即购买</button>
    <button class="zr-btn zr-btn--large zr-btn--danger">立即购买</button>
  </div>

  <div class="zr-panel-title">小号按钮</div>
  <div class="zr-panel" style="padding: 15px;">
    <button class="zr-btn zr-btn--small">取消订单</button>
    <button class="zr-btn zr-btn--small zr-btn--primary">确认付款</button>
  </div>

  <div class="zr-panel-title">迷你按钮</div>
  <div class="zr-panel" style="padding: 15px;">
    <button class="zr-btn zr-btn--mini zr-btn--plain">取消订单</button>
    <button class="zr-btn zr-btn--mini zr-btn--primary zr-btn--plain">确认付款</button>
    <button class="zr-btn zr-btn--mini zr-btn--warn zr-btn--plain">确认付款</button>
    <button class="zr-btn zr-btn--mini zr-btn--danger zr-btn--plain">确认付款</button>
  </div>

  <div class="zr-panel-title">Loading</div>
  <div class="zr-panel">
    <div class="zr-btns">
      <button class="zr-btn zr-btn--loading">取消订单</button>
      <button class="zr-btn zr-btn--loading zr-btn--primary">确认付款</button>
      <button class="zr-btn zr-btn--loading zr-btn--danger">确认付款</button>
      <button class="zr-btn zr-btn--loading zr-btn--warn">确认付款</button>
    </div>
  </div>

  <div class="zr-panel-title">Disabled</div>
  <div class="zr-panel">
    <div class="zr-btns">
      <button class="zr-btn zr-btn--disabled" disabled>取消订单</button>
      <button class="zr-btn zr-btn--disabled zr-btn--primary" disabled>确认付款</button>
      <button class="zr-btn zr-btn--disabled zr-btn--danger" disabled>确认付款</button>
      <button class="zr-btn zr-btn--disabled zr-btn--warn" disabled>确认付款</button>
    </div>
  </div>

</div>
</template>

<script>
export default {
  data () {
    return {
      data: '你好'
    }
  },
  components: {

  },
  methods: {
    tap () {
      this.data += '0'
    }
  },
  created () {
    console.log('created')
  }
}
</script>

<style >
.red {
    color: #F00;
}
</style>
