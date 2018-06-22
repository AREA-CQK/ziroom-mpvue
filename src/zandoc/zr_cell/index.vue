<template>

  <div class="container">

    <div class="doc-title zr-hairline--bottom">CELL</div>

    <div class="zr-panel">
      <div class="zr-cell">
        <div class="zr-cell__bd">单行列表</div>
      </div>
    </div>

    <div class="zr-panel">
      <div class="zr-cell">
        <div class="zr-cell__bd">单行列表</div>
        <div class="zr-cell__ft">详细信息</div>
      </div>
    </div>

    <div class="zr-panel">
      <div class="zr-cell">
        <div class="zr-cell__icon zr-icon zr-icon-checked" style="color:#38f;"></div>
        <div class="zr-cell__bd">单行列表</div>
        <div class="zr-cell__ft">详细信息</div>
      </div>
    </div>

    <div class="zr-panel">
      <div class="zr-cell">
        <div class="zr-cell__bd">
          <div class="zr-cell__text">单行列表</div>
          <div class="zr-cell__desc">附加描述</div>
        </div>
        <div class="zr-cell__ft">详细信息</div>
      </div>
    </div>

    <div class="zr-panel">
      <div class="zr-cell zr-cell--access">
        <div class="zr-cell__bd">单行列表</div>
        <div class="zr-cell__ft"></div>
      </div>
    </div>

    <div class="zr-panel">
      <div class="zr-cell zr-cell--switch">
        <div class="zr-cell__bd">开关</div>
        <div class="zr-cell__ft">
          <ZrSwitch v-bind="Object.assign({}, sw, {handleZrSwitchChange})"/>
        </div>
      </div>
    </div>

    <div class="zr-panel">
      <div class="zr-cell zr-cell--access">
        <div class="zr-cell__bd">单行列表</div>
        <div class="zr-cell__ft">详细信息</div>
      </div>
    </div>

    <div class="zr-panel">
      <div class="zr-cell">
        <div class="zr-cell__bd">多行列表</div>
      </div>
      <div class="zr-cell">
        <div class="zr-cell__bd">多行列表</div>
      </div>
      <div class="zr-cell">
        <div class="zr-cell__bd">多行列表</div>
      </div>
    </div>

    <div class="zr-panel">
      <div class="zr-cell">
        <div class="zr-cell__bd">多行列表</div>
        <div class="zr-cell__ft">详细信息</div>
      </div>
      <div class="zr-cell">
        <div class="zr-cell__bd">多行列表</div>
        <div class="zr-cell__ft">详细信息</div>
      </div>
      <div class="zr-cell">
        <div class="zr-cell__bd">多行列表</div>
        <div class="zr-cell__ft">详细信息</div>
      </div>
    </div>

    <div class="zr-panel">
      <div class="zr-cell zr-cell--access">
        <div class="zr-cell__bd">多行列表</div>
        <div class="zr-cell__ft"></div>
      </div>
      <div class="zr-cell zr-cell--access">
        <div class="zr-cell__bd">多行列表</div>
        <div class="zr-cell__ft"></div>
      </div>
      <div class="zr-cell zr-cell--access">
        <div class="zr-cell__bd">多行列表</div>
        <div class="zr-cell__ft"></div>
      </div>
    </div>

    <div class="zr-panel">
      <div class="zr-cell zr-cell--access">
        <div class="zr-cell__bd">多行列表</div>
        <div class="zr-cell__ft">详细信息</div>
      </div>
      <div class="zr-cell zr-cell--access">
        <div class="zr-cell__bd">多行列表</div>
        <div class="zr-cell__ft">详细信息</div>
      </div>
      <div class="zr-cell zr-cell--access">
        <div class="zr-cell__bd">多行列表</div>
        <div class="zr-cell__ft">详细信息</div>
      </div>
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
        sw: {
          checked: false,
          disabled: false,
          loading: false,
          componentId: 'sw',
          handleZrSwitchChange: null
        }
      }
    },
    methods: {
      handleZrSwitchChange (e) {
        this.sw.checked = e.checked
      }
    }
  }
</script>
<style >
</style>
<style  scoped>
</style>
