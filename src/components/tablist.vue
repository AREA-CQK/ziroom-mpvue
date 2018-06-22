<template>
  <div>
    <div
      v-for="item in list"
      :key="id"
      class="zr-tab__item"
      :class="{'zr-tab__item--selected': selectedId === item.id }"
      :data-component-id="componentId"
      :data-item-id="item.id"
      @click="__change"
    >
      <div class="zr-tab__title">{{ item.title }}</div>
    </div>
  </div>
</template>

<script>
  import {extractComponentId} from '../../utils/helper'
  export default {
    props: ['list', 'selectedId', 'componentId', '_handleZrTabChange'],
    methods: {
      __change (e) {
        const componentId = extractComponentId(e)
        const dataset = e.currentTarget.dataset
        const selectedId = dataset.itemId
        const data = { componentId, selectedId }
        this.$emit('change', data)
      }
    }
  }
</script>

<style scoped>

</style>
