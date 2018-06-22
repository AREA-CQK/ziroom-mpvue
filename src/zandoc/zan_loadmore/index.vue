<template>
  <div class="container">

    <div class="doc-title zr-hairline--bottom">LOADMORE</div>

    <ZrLoadmore v-bind="{ loading: true }" />
    <ZrLoadmore v-bind="{ nodata: true }" />
    <ZrLoadmore v-bind="{ nomore: true }" />
  </div>
</template>

<script>
  import ZrLoadmore from '../../components/zan/loadmore'
  export default {
    components: {
      ZrLoadmore
    },
    data () {
      return {}
    }
  }
</script>
<style  scoped>
</style>
