<template>
<div class="container">
  <img class="logo" src="https://img.yzcdn.cn/public_files/2017/02/06/ee0ebced79a80457d77ce71c7d414c74.png" />
  <div v-for="(group, idx) in list" :key="title">
        <div class="zr-panel-title">{{ group.title }}</div>
        <div class="zr-panel">
          <a v-for="(item, itemidx) in group.content" :key="name" class="zr-cell zr-cell--access" :href="item.path">
            <div class="zr-cell__bd">{{ item.name }}</div>
            <div class="zr-cell__ft"></div>
          </a>
        </div>
  </div>
</div>
</template>

<script>
import componentsConfig from './config'
export default {
  data () {
    return {
      list: componentsConfig
    }
  },
  methods: {

  }
}
</script>

<style  scoped>
.logo {
    display: block;
    margin: 40px auto;
    width: 92px;
    height: 82px;
}
</style>
