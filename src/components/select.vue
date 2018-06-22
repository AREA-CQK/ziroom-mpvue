<template>
  <radio-group
    class="zr-select__list"
    :name=" name || componentId || ''"
    @change="_handleZrSelectChange"
    :data-component-id="componentId"
  >
    <label v-for="item in items" :key="value">
      <div class="zr-cell">
        <radio class="zr-select__radio" :value="item.value" :checked="item.value === checkedValue"></radio>
        <div
          class="zr-cell__bd"
          :style="'padding-left' + maohao + item.padding + 'px;'
          +'color' + maohao + ((item.value === checkedValue) && (activeColor || '#ff4444'))+ ';'"
        >{{ item.name }}</div>
        <div v-if="item.value === checkedValue" class="zr-cell__ft">
          <icon type="success_no_circle" :color="getColor" size="14"></icon>
        </div>
      </div>
    </label>
  </radio-group>
</template>

<script>
  import {extractComponentId} from '../../utils/helper'
  const maohao = ':'
  export default {
    props: {
      name: {
        type: String,
        default: ''
      },
      componentId: {
        type: String,
        default: ''
      },
      items: {
        type: Array,
        default: []
      },
      checkedValue: {
        type: String,
        default: ''
      },
      activeColor: {
        type: String,
        default: '#ff4444'
      }
    },

    data () {
      return {}
    },
    computed: {
      maohao: function () {
        return maohao
      },
      getColor: function () {
        return this.activeColor || '#ff4444'
      }
    },
    methods: {
      _handleZrSelectChange (e) {
        this.handle(e)
      },
      handle (e) {
        const componentId = extractComponentId(e)
        const value = e.target.value
        this.callback(componentId, value)
      },
      callback (componentId, value) {
        const e = {componentId, value}
        console.info('[zan:Select:change]', e)
        this.$emit('handleZrSelectChange', e)
      }
    }
  }

</script>

<style scoped>

</style>
