<template>

  <div class="container">

    <div class="doc-title zr-hairline--bottom">SWITCH</div>

    <div class="zr-panel-title">同步开关</div>
    <div class="zr-panel">
      <ZrSwitch v-bind="sync" :componentId="'sync'" />
    </div>

    <div class="zr-panel-title">异步开关</div>
    <div class="zr-panel">
      <ZrSwitch v-bind="async" :componentId="'async'" />
    </div>

    <div class="zr-panel-title">开关不可用</div>
    <div class="zr-panel">
      <ZrSwitch v-bind="{ checked: false, disabled: true, componentId: 'switch3', styles: 'margin-right: 8px;' }" />
      <ZrSwitch v-bind="{ checked: true, disabled: true, componentId: 'switch4' }" />
    </div>

  </div>
</template>

<script>
  import ZrSwitch from '../../components/zan/switch'
  export default {
    components: {
      ZrSwitch
    },
    data () {
      return {
        sync: {
          checked: false,
          handleZrSwitchChange: this.handleZrSwitchChange
        },
        async: {
          checked: true,
          loading: false,
          handleZrSwitchChange: this.handleZrSwitchChange
        }
      }
    },
    methods: {
      handleZrSwitchChange (e) {
        console.log(this)
        const componentId = e.componentId
        const checked = e.checked

        if (componentId === 'sync') {
          // 同步开关
          this[componentId].checked = checked
        } else if (componentId === 'async') {
          // 异步开关
          this[componentId].loading = true
          setTimeout(() => {
            this[componentId].loading = false
            this[componentId].checked = checked
          }, 500)
        }
      }
    }
  }
</script>
<style  scoped >
  .zr-panel {
    padding: 10px;
  }
  /*.zr-switch {*/
    /*margin-right: 8px;*/
  /*}*/
</style>
