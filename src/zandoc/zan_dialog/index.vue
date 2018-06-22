<template>
  <div class="container">

    <div class="doc-title zr-hairline--bottom">DIALOG</div>

    <div class="zr-btns" style="margin-top: 30vh;">
      <button class="zr-btn" @click="toggleBaseDialog">基础 Dialog</button>
      <button class="zr-btn" @click="toggleWithoutTitleDialog">Dialog - 无标题</button>
      <button class="zr-btn" @click="toggleButtonDialog">Dialog - 自定义显示按钮</button>
      <button class="zr-btn" @click="toggleVerticalDialog">Dialog - 按钮纵向排布</button>
    </div>
    <ZrDialog v-bind="zanDialog"/>
  </div>
</template>
<script>
  import ZrDialog from '../../components/zan/dialog'
  export default {
    components: {
      ZrDialog
    },
    data () {
      return {
        zanDialog: {
          'name': '',
          'show': false,
          'title': '',
          'content': '',
          'buttons': [],
          'buttonsShowVertical': true,
          res: {}
        }
      }
    },
    methods: {
      ...ZrDialog.methods,
      toggleBaseDialog () {
        const obj = {
          title: '弹窗',
          content: '这是一个模态弹窗',
          showCancel: true
          // date: new Date()
        }
        this.showZrDialog(obj).then(() => {
          console.log('=== dialog ===', 'type: confirm')
        }).catch(() => {
          console.log('=== dialog ===', 'type: cancel')
        })
      },

      toggleWithoutTitleDialog () {
        const obj = {
          content: '这是一个模态弹窗'
        }
        this.showZrDialog(obj).then(() => {
          console.log('=== dialog without title === type: confirm')
        })
      },

      toggleButtonDialog () {
        const obj = {
          title: '弹窗',
          content: '这是一个模态弹窗',
          buttons: [{
            text: '现金支付',
            color: 'red',
            type: 'cash'
          }, {
            text: '微信支付',
            color: '#3CC51F',
            type: 'wechat'
          }, {
            text: '取消',
            type: 'cancel'
          }]
        }
        this.showZrDialog(obj).then(({type}) => {
          console.log('=== dialog with custom buttons === type: ' + type)
        })
      },

      toggleVerticalDialog () {
        const obj = {
          title: '弹窗',
          content: '这是一个模态弹窗',
          buttonsShowVertical: true,
          buttons: [{
            text: '现金支付',
            color: 'red',
            type: 'cash'
          }, {
            text: '微信支付',
            color: '#3CC51F',
            type: 'wechat'
          }, {
            text: '取消',
            type: 'cancel'
          }]
        }
        this.showZrDialog(obj).then(({type}) => {
          console.log('=== dialog with vertical buttons === type: ' + type)
        })
      }
    }
  }
</script>
<style  scoped>
</style>
