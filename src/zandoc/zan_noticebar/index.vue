<template>
  <div class="container">
    <div class="doc-title zr-hairline--bottom" @click="onclick">NOTICEBAR</div>

    <div class="zr-panel-title">滚动通告栏</div>
    <div class="zr-panel">
      <zanbar v-on:ref="setRef" v-bind="movable"  :componentId="'movable'"/>
    </div>

    <div class="zr-panel-title">静止通告栏1</div>
    <div class="zr-panel">
      <zanbar v-bind="this.static1" :componentId="'static1'"/>
    </div>

    <div class="zr-panel-title">静止通告栏2</div>
    <div class="zr-panel">
      <zanbar v-bind="this.static2" :componentId="'static2'"/>
    </div>
  </div>
</template>

<script>
  import ZrNoticeBar from '../../components/zan/noticebar'
  export default {
    components: {
      zanbar: ZrNoticeBar
    },
    data () {
      return {
        movable: {
          text: '足协杯战线连续第2年上演广州德比战，上赛季半决赛上恒大以两回合5-3的总比分淘汰富力。',
          animationData: []
        },
        static1: {
          text: '足协杯战线连续第2年上演广州德比战',
          animationData: []
        },
        static2: {
          text: '足协杯战线连续第2年上演广州德比战，上赛季半决赛上恒大以两回合5-3的总比分淘汰富力。',
          animationData: []
        }
      }
    },
    methods: {
      ...ZrNoticeBar.methods,
      setRef: function (payload) {
        console.log(payload)
        // this.initZrNoticeBarScroll = payload['movable'].initZrNoticeBarScroll
        // this.scrollZrNoticeBar = payload['movable'].scrollZrNoticeBar
        // 滚动通告栏需要initScroll
        setTimeout(() => {
          var that = this
          this.initZrNoticeBarScroll(that, 'movable')
          // initScroll的通告栏如果宽度足够显示内容将保持静止
          this.initZrNoticeBarScroll(that, 'static1')
          // 不进行initScroll的通告栏也将保持静止
          // this.initZrNoticeBarScroll('static2');
        }, 500)
      }
    }
  }
</script>
<style  scoped>
</style>
