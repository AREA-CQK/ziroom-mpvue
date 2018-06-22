<template>
  <div class="container" >
    <button class="weui-btn weui-btn-primary" @click="showModel = !showModel">show Modal</button>
    <Modal text="测试" :show="showModel" @commit="commitHandle" @cancel="cancelHandle"/>
  </div>
</template>

<script>
import Modal from '../../components/modal'
export default {
  data () {
    return {
      userInfo: {},
      showModel: false
    }
  },

  components: {
    Modal
  },

  methods: {
    getUserInfo () {
      // 调用登录接口
      wx.login({
        success: () => {
          wx.getUserInfo({
            success: (res) => {
              this.userInfo = res.userInfo
            }
          })
        }
      })
    },
    commitHandle () {
      console.log('确定')
    },
    cancelHandle () {
      console.log('取消')
    }
  },
  mounted () {
    
  },
  created () {
    // 调用应用实例的方法获取全局数据
    this.getUserInfo()
  }

}
</script>

<style scoped>
  
</style>
