<template>
  <div class="zr-actionsheet" :class="{'zr-actionsheet--show': show }">
    <div
      class="zr-actionsheet__mask"
      @click="_handlezrActionsheetMaskClick"
      :data-close-on-click-overlay="closeOnClickOverlay"
      :data-component-id="componentId"></div>
    <div class="zr-actionsheet__container">
      <!-- 实际按钮显示 -->
      <button
        v-for="(item, index) in actions"
        :key="index + '-' + item.name"
        @click="_handlezrActionsheetBtnClick"
        :data-component-id="componentId"
        :data-index="index"
        :open-type="item.openType"
        class="zr-btn zr-actionsheet__btn"
        :class="computedClassStr[index]"
      >
        <text>{{ item.name }}</text>
        <text
          v-if="item.subname"
          class="zr-actionsheet__subname">{{ item.subname }}
        </text>
      </button>

      <!-- 关闭按钮 -->
      <div
        v-if="cancelText"
        class="zr-actionsheet__footer"
      >
        <button
          class="zr-btn zr-actionsheet__btn"
          @click="_handlezrActionsheetCancelBtnClick"
          :data-component-id="componentId"
        >{{ cancelText }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
  import {extractComponentId} from '../../utils/helper'

  export default {
    props: {
      show: Boolean,
      cancelText: String,
      closeOnClickOverlay: Boolean,
      componentId: String,
      actions: Array,
      handlezrActionsheetClick: Boolean,
      handlezrActionsheetCancel: Boolean
    },
    data () {
      return {
        // show: false,
        // cancelText: '关闭 Action',
        // closeOnClickOverlay: true,
        // componentId: 'baseActionsheet',
        // actions: [{
        //   name: '选项0',
        //   subname: '选项描述语1',
        //   className: 'action-class',
        //   loading: false
        // }, {
        //   name: '选项1',
        //   subname: '选项描述语2',
        //   className: 'action-class',
        //   loading: false
        // }, {
        //   name: '去分享',
        //   openType: 'share'
        // }]
      }
    },
    computed: {
      computedClassStr: function () {
        if (!this.actions) return null
        let arr = []
        for (let i = 0; i < this.actions.length; i++) {
          let str = this.actions[i].className + ' ' + (this.actions[i].loading ? 'zr-btn--loading' : '')
          arr.push(str)
        }
        return arr
      }
    },
    methods: {
      _handlezrActionsheetMaskClick ({currentTarget = {}}) {
        const dataset = currentTarget.dataset || {}
        const {componentId, closeOnClickOverlay} = dataset

        // 判断是否在点击背景时需要关闭弹层
        if (!closeOnClickOverlay) {
          return
        }

        this.resolveCancelClick({componentId})
      },

      _handlezrActionsheetCancelBtnClick (e) {
        const componentId = extractComponentId(e)

        this.resolveCancelClick({componentId})
      },

      _handlezrActionsheetBtnClick ({currentTarget = {}}) {
        const dataset = currentTarget.dataset || {}
        const {componentId, index} = dataset
        if (this.handlezrActionsheetClick) {
          // this.handlezrActionsheetClick({componentId, index})
          this.$emit('handlezrActionsheetClick', {componentId, index})
        } else {
          console.warn('页面缺少 handlezrActionsheetClick 回调函数')
        }
      },
      resolveCancelClick ({componentId}) {
        console.info('[zr:actionsheet:cancel]')
        if (this.handlezrActionsheetCancel) {
          // this.handlezrActionsheetClick({componentId, index})
          this.$emit('handlezrActionsheetCancel', {componentId})
        } else {
          console.warn('页面缺少 handlezrActionsheetCancel 回调函数')
        }
      }
    }
  }
</script>

<style scoped>

</style>
