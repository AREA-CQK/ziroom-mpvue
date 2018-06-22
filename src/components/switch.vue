<template name="zr-switch">
  <div
    class="zr-switch"
    :class="computedClassStr"
    :data-checked="checked"
    :data-loading="loading"
    :data-disabled="disabled"
    :data-component-id="componentId"
    :style="styles || ''"
    @click="_handleZrSwitchChange"
  >
    <div class="zr-switch__circle">
      <div :hidden="!loading" class="zr-switch__loading"></div>
    </div>
    <div class="zr-switch__bg"></div>
  </div>
</template>


<script>
  export default {
    props: [
      'checked',
      'disabled',
      'loading',
      'componentId',
      'handleZrSwitchChange',
      'styles'
    ],
    computed: {
      computedClassStr: function () {
        return 'zr-switch--' + (this.checked ? 'on' : 'off') + ' ' + (this.disabled ? 'zr-swtich--disabled' : '')
      }
    },
    methods: {
      _handleZrSwitchChange (e) {
        const dataset = e.currentTarget.dataset
        console.log(dataset)
        const checked = !dataset.checked
        const loading = dataset.loading
        const disabled = dataset.disabled
        const componentId = dataset.componentId

        if (loading || disabled) return

        console.info('[zan:switch:change]', { checked, componentId })

        if (this.handleZrSwitchChange) {
          this.handleZrSwitchChange({
            checked,
            componentId
          })
        } else {
          console.warn('页面缺少 handleZrSwitchChange 回调函数')
        }
      }
    }
  }
</script>
