<template>

  <div class="container">

    <div class="doc-title zr-hairline--bottom">STEPS</div>

    <div class="zr-panel">
      <div class="zr-cell">
        <div class="zr-cell__bd">
          <ZrSteps v-bind="{ steps: steps }"/>
        </div>
      </div>

      <div class="zr-cell">
        <div class="zr-cell__bd">
          <ZrSteps v-bind="{ type: 'horizon', steps: steps2 }"/>
        </div>
      </div>

      <div class="zr-cell zr-cell--last-child">
        <div class="zr-cell__bd">
          <ZrSteps v-bind="{ type: 'horizon', steps: steps3 }"/>
        </div>
      </div>
    </div>

    <div class="zr-panel-title">有描述的steps</div>
    <div class="zr-panel">
      <div class="zr-cell">
        <div class="zr-cell__bd">
          <ZrSteps v-bind="{ type: 'horizon', hasDesc: true, steps: steps }"/>
        </div>
      </div>

      <div class="zr-cell">
        <div class="zr-cell__bd">
          <ZrSteps v-bind="{ type: 'horizon', hasDesc: true, steps: steps2 }"/>
        </div>
      </div>

      <div class="zr-cell zr-cell--last-child">
        <div class="zr-cell__bd">
          <ZrSteps v-bind="{ type: 'horizon', hasDesc: true, steps: steps3 }"/>
        </div>
      </div>
    </div>

    <div class="zr-panel-title">垂直方向的steps</div>
    <div class="zr-panel">
      <div class="zr-cell zr-cell">
        <div class="zr-cell__bd">
          <ZrSteps v-bind="{ type: 'vertical', hasDesc: true, steps }"/>
        </div>
      </div>

      <div class="zr-cell zr-cell--last-child">
        <div class="zr-cell__bd">
          <ZrSteps v-bind="{ type: 'vertical', steps }"/>
        </div>
      </div>
    </div>

    <div class="zr-panel-title">可自定义class</div>
    <div class="zr-panel">
      <div class="zr-cell__bd">
        <ZrSteps v-bind="{ type: 'vertical', steps, className: 'my-class' }"/>
      </div>
    </div>

  </div>

</template>

<script>
  import ZrSteps from '../../components/zan/steps'
  export default {
    components: {
      ZrSteps
    },
    data () {
      return {
        steps: [
          {
            current: true,
            done: true,
            text: '步骤一',
            desc: '10.01'
          },
          {
            done: false,
            current: false,
            text: '步骤二',
            desc: '10.02'
          },
          {
            done: false,
            current: false,
            text: '步骤三'
          }
        ],
        steps2: [
          {
            current: false,
            done: true,
            text: '步骤一',
            desc: '10.01'
          },
          {
            done: true,
            current: true,
            text: '步骤二',
            desc: '10.02'
          },
          {
            done: false,
            current: false,
            text: '步骤三',
            desc: '10.03'
          }
        ],
        steps3: [
          {
            current: false,
            done: true,
            text: '步骤一',
            desc: '10.01'
          },
          {
            done: true,
            current: false,
            text: '步骤二',
            desc: '10.02'
          },
          {
            done: true,
            current: true,
            text: '步骤三',
            desc: '10.03'
          }
        ]
      }
    },
    methods: {
      handleZrStepperChange (e) {
        const {componentId, stepper} = e
        this[componentId].stepper = stepper
      }
    }
  }
</script>
<style  scoped >

</style>
