<template>
  <div class="container" >
    <button class="zr-btn zr-btn--primary" >Button</button>
     <button class="zr-btn" @click="toggleLeftPopup">
        从左边弹出popup
      </button>
      <button class="zr-btn" @click="showToast">
        显示toast
      </button>
      <div class="popup-example--left zr-popup zr-popup--left" :class="{ 'zr-popup--show': showLeftPopup }">
      <div class="zr-popup__mask" @click="toggleLeftPopup"></div>
      <div class="zr-popup__container">
        <div class="zr-btns">
          <button class="zr-btn" @click="toggleLeftPopup">
            关闭 popup
          </button>
        </div>
      </div>
    </div>

     <_toast />
  </div>
</template>

<script>
import './index.scss'
import { getComponentByTag } from '../../utils/helper'
import Zrtoast from '../../components/toast'
export default {
  data () {
    return {
      userInfo: {},
      showPopup: false,
      showLeftPopup: false,
    }
  },

  components: {
    _toast : Zrtoast
  },

  methods: {
    
  toggleLeftPopup () {
      this.showLeftPopup = !this.showLeftPopup
  },
  showToast () {
      this.toast.showZrToast('toast的内容')
  },
  },
  mounted () {
    this.toast = getComponentByTag(this, '_toast')
  },
  created () {
    
  }

}
</script>

<style scoped>
.popup-example--left .zr-popup__container {
    top: 0;
    bottom: 0;
  }
</style>
