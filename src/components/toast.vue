<template>
  <div
    class="zr-toast"
    :class="{ 'zr-toast--notitle' : !zanToast.title }"
    v-if="zanToast.show"
    @click="clearZrToast"
  >
    <!-- icon 展示 -->
    <div v-if="zanToast.icon || zanToast.image">
      <div
        v-if="zanToast.image"
        class="zr-toast__icon zr-toast__icon-image"
        :style="computedStyleStr"
      ></div>
      <div
        v-else-if="zanToast.icon === 'loading'"
        class="zr-toast__icon zr-toast__icon-loading"
      >
        <div class="zr-loading"></div>
      </div>
      <div
        v-else
        class="zr-toast__icon zr-icon"
        :class="'zr-icon-' + zanToast.icon"
      ></div>
    </div>

    <!-- 文案展示 -->
    <div v-if="zanToast.title">{{ zanToast.title }}</div>
  </div>
</template>

<script>
  export default {
    computed: {
      computedStyleStr: function () {
        return `background-image: url(${this.zanToast.image});`
      }
    },
    data () {
      return {
        zanToast: {}
      }
    },
    methods: {
      showZrToast (title, timeout) {
        console.log(this)
        const options = formatParameter(title, timeout)

          // 清除上一轮的计时器
        const { timer = 0 } = this.zanToast || {}
        clearTimeout(timer)

          // 弹层设置~
        const z = {
          show: true,
          icon: options.icon,
          image: options.image,
          title: options.title
        }
        this.zanToast = z
          // 传入的显示时长小于0，就认为需要一直显示
        if (timeout < 0) {
          return
        }

            // 下一轮计时器
        const nextTimer = setTimeout(() => {
          this.clearZrToast()
        }, timeout || 3000)

        this.zanToast.timer = nextTimer
      },

          // 清除所有 toast
      clearZrToast () {
        const { timer = 0 } = this.zanToast || {}
        clearTimeout(timer)

        this.zanToast.show = false
      },

          // 快捷方法，显示 loading
      showZrLoading (title) {
        const options = formatParameter(title)

        this.showZrToast({
          ...options,
          icon: 'loading'
        })
      }
    }
  }
  function formatParameter (title, timeout = 0) {
    // 如果传入的 title 是对象，那么认为所有的配置属性都在这个对象中了
    if (typeof title === 'object') {
      return title
    }

    return {
      title,
      timeout
    }
  }
</script>

<style scoped>

</style>
