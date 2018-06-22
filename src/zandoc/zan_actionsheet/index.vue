<template>
  <div class="container">

    <div class="doc-title zr-hairline--bottom zr-hairline--bottom">ACTIONSHEET</div>

    <div class="zr-btns" style="margin-top: 30vh;">
      <button class="zr-btn" @click="toggleActionsheet">
        Actionsheet
      </button>
    </div>

    <Actionsheet
      v-bind="baseActionsheet"
      :handleZrActionsheetClick="true"
      :handleZrActionsheetCancel="true"
      v-on:handleZrActionsheetClick="handleZrActionsheetClick"
      v-on:handleZrActionsheetCancel="handleZrActionsheetCancel"/>
  </div>
</template>

<script>
  import Actionsheet from '../../components/zan/actionsheet'

  export default {
    components: {
      Actionsheet
    },
    data () {
      return {
        baseActionsheet: {
          show: false,
          cancelText: '关闭 Action',
          closeOnClickOverlay: true,
          componentId: 'baseActionsheet',
          actions: [{
            name: '选项1',
            subname: '选项描述语1',
            className: 'action-class',
            loading: false
          }, {
            name: '选项2',
            subname: '选项描述语2',
            className: 'action-class',
            loading: false
          }, {
            name: '去分享',
            openType: 'share'
          }]
        }
      }
    },
    methods: {
      onShareAppMessage () {
        return {
          title: 'ZrUI-WeApp',
          imageUrl: 'https://img.yzcdn.cn/public_files/2017/02/06/ee0ebced79a80457d77ce71c7d414c74.png'
        }
      },

      toggleActionsheet () {
        this.baseActionsheet.show = true
      },
      handleZrActionsheetCancel ({componentId}) {
        this[componentId].show = false
      },
      handleZrActionsheetClick ({componentId, index}) {
        console.log('item index ' + index + ' clicked')
        // 如果是分享按钮被点击, 不处理关闭
        if (index === 2) {
          return
        }
        this[componentId].actions[index].loading = true
        setTimeout(() => {
          this[componentId].show = false
          this[componentId].actions[index].loading = false
        }, 1500)
      }
    }
  }

</script>
<style >
</style>
<style  scoped>
</style>
