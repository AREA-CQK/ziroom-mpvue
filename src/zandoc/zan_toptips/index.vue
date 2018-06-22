<template>
  <view class="container">

    <view class="doc-title zr-hairline--bottom">TOPTIPS</view>

    <view class="zr-btns" style="margin-top: 30vh;">
      <button class="zr-btn" @click="showTopTips">
        显示toptips
      </button>
    </view>
    <toptips />
  </view>


</template>

<script>
  import { getComponentByTag } from '../../utils/helper'
  import ZrTopTips from '../../components/zan/toptips'
  export default {
    components: {
      toptips: ZrTopTips
    },
    data () {
      return {
        zanTopTips: {}
      }
    },
    methods: {
      showTopTips () {
        getComponentByTag(this, 'toptips').showZrTopTips('toptips的内容')
      }
    }
  }
</script>
<style  scoped >

</style>
