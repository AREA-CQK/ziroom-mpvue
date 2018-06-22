<template>
  <div class="zr-tab">
    <block v-if="scroll || false">
      <scroll-view
        class="zr-tab__bd zr-tab__bd--scroll"
        :class="{ 'zr-tab__bd--fixed' : fixed }"
        scroll-x="true"
        :style="'height' + mao +  height + 'px auto'"
      >
        <ZrTabList v-bind="{ list , selectedId, componentId }" @change="_change"/>
      </scroll-view>
    </block>
    <block wx:else>
      <div class="zr-tab__bd" :class="{ 'zr-tab__bd--fixed' : fixed }">
        <ZrTabList v-bind="{ list, selectedId, componentId }" @change="_change"/>
      </div>
    </block>
  </div>
</template>


<script>
  import ZrTabList from './tablist'
  const maohao = ':'
  export default {
    props: ['scroll', 'fixed', 'height', 'list', 'selectedId', 'componentId'],
    components: {
      ZrTabList
    },
    computed: {
      mao: function () {
        return maohao
      }
    },
    data () {
      return {
        list: [],
        selectedId: '',
        componentId: ''
      }
    },
    methods: {
      _change (data) {
        this.$emit('change', data)
      }
    }
  }
</script>

<style scoped>

</style>
