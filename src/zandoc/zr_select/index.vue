<template>

  <div class="container">

    <div class="doc-title zr-hairline--bottom">SELECT</div>

    <div class="zr-panel-title">基础用法</div>
    <div class="zr-panel">
      <div>
        <zr-select v-bind="{ items, checkedValue: checked.base, componentId: 'base'}" @handleZrSelectChange="handleZrSelectChange"/>
      </div>
    </div>

    <div class="zr-panel-title">自定义高亮颜色</div>
    <div class="zr-panel">
      <div>
        <zr-select v-bind="{ items, checkedValue: checked.color, activeColor, componentId: 'color'}" @handleZrSelectChange="handleZrSelectChange"/>
      </div>
    </div>

    <div class="zr-panel-title">Form 表单中的select应用</div>
    <form @submit="formSubmit">
      <div class="zr-panel">
        <div>
          <zr-select v-bind="{ items, checkedValue: checked.form, name: 'formtest', componentId: 'form'}"  @handleZrSelectChange="handleZrSelectChange"/>
        </div>
      </div>

      <div class="zr-btns">
        <button
          class="zr-btn zr-btn--primary"
          formType="submit">提交数据</button>
      </div>
    </form>
    <toptips />
  </div>
</template>

<script>
  import { getComponentByTag } from '../../utils/helper'
  import ZrSelect from '../../components/zan/select'
  import ZrTopTips from '../../components/zan/toptips'
  export default {
    components: {
      ZrSelect,
      toptips: ZrTopTips
    },
    data () {
      return {
        items: [
          {
            padding: 0,
            value: '1',
            name: '选项一'
          },
          {
            padding: 0,
            value: '2',
            name: '选项二'
          }
        ],

        checked: {
          base: '-1',
          color: '-1',
          form: '-1'
        },
        activeColor: '#4b0'
      }
    },
    methods: {
      handleZrSelectChange ({ componentId, value }) {
        this.checked[componentId] = value
      },

      formSubmit (event) {
        console.log('[zan:field:submit]', event.target.value)
        getComponentByTag(this, 'toptips').showZrTopTips(`选中的值为${event.target.value.formtest}`)
      }
    }
  }
</script>
<style  scoped>
</style>
