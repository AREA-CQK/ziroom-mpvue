<template >
  <div class="zr-stepper"
   :class="{'zr-stepper--small': size === 'small'}">
    <div
      class="zr-stepper__minus"
      :class="{'zr-stepper--disabled': stepper <= min }"
      :data-component-id="componentId"
      :data-stepper="stepper"
      :data-disabled="stepper <= min"
      @click="_handleZrStepperMinus"
    >-</div>
    <input
      class="zr-stepper__text"
      :class="{ 'zr-stepper--disabled' : min >= max }"
      type="number"
      :data-component-id="componentId"
      :data-min="min"
      :data-max="max"
      :value="stepper"
      :disabled="min >= max"
      @blur="_handleZrStepperBlur"
    />
    <div
      class="zr-stepper__plus"
      :class="{ 'zr-stepper--disabled' : stepper >= max }"
      :data-component-id="componentId"
      :data-stepper="stepper"
      :data-disabled="stepper >= max"
      @click="_handleZrStepperPlus"
    >+</div>
  </div>
</template>

<script>
  export default {
    props: {
      componentId: {
        type: String,
        default: ''
      },
      size: {
        type: String,
        default: ''
      },
      stepper: {
        type: Number,
        default: 0
      },
      min: {
        type: Number,
        default: 0
      },
      max: {
        type: Number,
        default: 10
      }
    },
    methods: {
      _handleZrStepperMinus (e) {
        this.handle(e, -1)
      },

      _handleZrStepperPlus (e) {
        this.handle(e, +1)
      },

      _handleZrStepperBlur: function (e) {
        var dataset = e.currentTarget.dataset
        var componentId = dataset.componentId
        var max = +dataset.max
        var min = +dataset.min
        var value = e.target.value

        if (!value) {
          setTimeout(() => {
            this.callback(componentId, min)
          }, 16)
          this.callback(componentId, value)
          return '' + value
        }

        value = +value
        if (value > max) {
          value = max
        } else if (value < min) {
          value = min
        }

        this.callback(componentId, value)

        return '' + value
      },
      handle (e, num) {
        var dataset = e.currentTarget.dataset
        var componentId = dataset.componentId
        var disabled = dataset.disabled
        var stepper = +dataset.stepper

        if (disabled) return null

        this.callback(componentId, stepper + num)
      },

      callback (componentId, stepper) {
        stepper = +stepper
        var e = {componentId, stepper}
        console.info('[zan:stepper:change]', e)
        this.$emit('handleZrStepperChange', e)
      }
    }
  }
</script>

<style scoped>

</style>
