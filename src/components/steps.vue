<template>
  <div class="zr-steps"
       :class="getClassStr">
    <div
      v-for="(step, index) in steps" :key="unique"
      class="zr-steps__step"
      :class="{ 'zr-steps__step--db-title' : hasDesc , 'zr-steps__step--first-child' : index === 0 , 'zr-steps__step--last-child' : index === steps.length - 1, 'zr-steps__step--done' : step.done ,
        'zr-steps__step--cur' : step.current  }"
    >
      <div class="zr-steps__title">{{ step.text }}</div>
      <div v-if="hasDesc && step.desc " class="zr-steps__title zr-steps__title--desc">{{ step.desc }}</div>
      <div class="zr-steps__icons">
        <div class="zr-steps__circle"></div>
      </div>
      <div class="zr-steps__line"></div>
    </div>
  </div>
</template>


<script>
    export default {
      props: ['type', 'vsteps', 'steps', 'className', 'hasDesc'],
      computed: {
        getClassStr: function () {
          let str = 'zr-steps--'
          str += (this.type === 'vertical' ? 'vsteps' : 'steps')
          str += ' zr-steps--' + this.steps.length + ' ' + (this.className || '')
          return str
        }
      }
    }
</script>

<style scoped>
  .my-class {
    padding: 10px;
  }
  .my-class .zr-steps__step--done {
    color: #f44;
  }
</style>
