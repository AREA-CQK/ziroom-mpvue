<template>
  <div class="container">

    <div class="doc-title zr-hairline--bottom">POPUP</div>

    <div class="zr-btns" style="margin-top: 30vh;">
      <button class="zr-btn" @click="togglePopup">
        弹出popup
      </button>
      <button class="zr-btn" @click="toggleTopPopup">
        从顶部弹出popup
      </button>
      <button class="zr-btn" @click="toggleBottomPopup">
        从底部弹出popup
      </button>
      <button class="zr-btn" @click="toggleLeftPopup">
        从左边弹出popup
      </button>
      <button class="zr-btn" @click="toggleRightPopup">
        从右边弹出popup
      </button>
    </div>

    <div class="zr-popup" :class="{ 'zr-popup--show': showPopup }">
      <div class="zr-popup__mask" @click="togglePopup"></div>
      <div class="zr-popup__container popup-example--center">
        <div class="zr-btns">
          <button class="zr-btn" @click="togglePopup">
            关闭 popup
          </button>
        </div>
      </div>
    </div>

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

    <div class="popup-example--right zr-popup zr-popup--right" :class="{ 'zr-popup--show' : showRightPopup }">
      <div class="zr-popup__mask" @click="toggleRightPopup"></div>
      <div class="zr-popup__container">
        <div class="zr-btns">
          <button class="zr-btn" @click="toggleRightPopup">
            关闭 popup
          </button>
        </div>
      </div>
    </div>

    <div class="popup-example--top zr-popup zr-popup--top" :class="{ 'zr-popup--show' : showTopPopup }">
      <div class="zr-popup__mask" @click="toggleTopPopup"></div>
      <div class="zr-popup__container">
        内容
      </div>
    </div>

    <div class="popup-example--bottom zr-popup zr-popup--bottom" :class="{ 'zr-popup--show' : showBottomPopup }">
      <div class="zr-popup__mask" @click="toggleBottomPopup"></div>
      <div class="zr-popup__container">
        <div class="zr-btns">
          <button class="zr-btn" @click="toggleBottomPopup">
            关闭 popup
          </button>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
  export default {
    data () {
      return {
        showPopup: false,
        showLeftPopup: false,
        showRightPopup: false,
        showTopPopup: false,
        showBottomPopup: false
      }
    },
    methods: {
      togglePopup () {
        this.showPopup = !this.showPopup
      },

      toggleLeftPopup () {
        this.showLeftPopup = !this.showLeftPopup
      },

      toggleRightPopup () {
        this.showRightPopup = !this.showRightPopup
      },

      toggleBottomPopup () {
        this.showBottomPopup = !this.showBottomPopup
      },

      toggleTopPopup () {
        this.showTopPopup = !this.showTopPopup
      }
    }
  }
</script>
<style  scoped>
  .popup-example--center {
    border-radius: 4px;
  }

  .popup-example--right .zr-popup__container {
    top: 0;
    bottom: 0;
  }

  .popup-example--left .zr-popup__container {
    top: 0;
    bottom: 0;
  }

  .popup-example--top .zr-popup__container {
    left: 0;
    right: 0;
    padding: 15px;
    background-color: rgba(0, 0, 0, 0.7);
    color: #fff;
    font-size: 16px;
  }
  .popup-example--top .zr-popup__mask {
    opacity: 0;
  }

  .popup-example--bottom .zr-popup__container {
    left: 0;
    right: 0;
  }
</style>
