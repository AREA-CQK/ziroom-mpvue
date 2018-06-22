<template>
  <div class="container">

    <view class="doc-title zr-hairline--bottom">Tag</view>

    <view class="zr-panel">
      <view class="zr-cell zr-cell--last-child">
        <view class="zr-tag">灰色</view>
        <view class="zr-tag zr-tag--danger">红色</view>
        <view class="zr-tag zr-tag--disabled">不可用</view>
      </view>
    </view>
    <view class="zr-panel">
      <view class="zr-cell zr-cell--last-child">
        <view class="zr-tag zr-tag--danger">会员折扣</view>
        <view class="zr-tag zr-tag--warn">返现</view>
        <view class="zr-tag zr-tag--primary">返现</view>
        <view class="zr-tag zr-tag--primary zr-tag--disabled">不可用</view>
      </view>
    </view>

    <view class="zr-panel">
      <view class="zr-cell zr-cell--last-child">
        <view class="zr-tag zr-tag--plain">灰色</view>
        <view class="zr-tag zr-tag--danger zr-tag--plain">会员折扣</view>
        <view class="zr-tag zr-tag--warn zr-tag--plain">返现</view>
        <view class="zr-tag zr-tag--primary zr-tag--plain">返现</view>
        <view class="zr-tag zr-tag--primary zr-tag--plain zr-tag--disabled">返现不可用</view>
      </view>
    </view>
  </div>
</template>

<script>
  export default {
  }
</script>
<style  scoped >
  .zr-tag + .zr-tag {
    margin-left: 10px;
  }
</style>
