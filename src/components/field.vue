<template>
    <div class="zr-cell zr-field"
         :class="{ 'zr-field--error': error , 'zr-field--wrapped': mode === 'wrapped' }">
      <div
        v-if="title"
        class="zr-cell__hd zr-field__title">{{ title }}</div>
      <textarea
        v-if="type === 'textarea'"
        auto-height
        :name="name || componentId || ''"
        :value="value"
        :focus="focus"
        :key="'textarea-'+componentId"
        :placeholder="placeholder"
        class="zr-field__input zr-cell__bd"
        :class="{ 'zr-field__input--right' : right }"
        placeholder-class="zr-field__placeholder"
        @input="_handleZrFieldChange"
        @focus="_handleZrFieldFocus"
        @blur="_handleZrFieldBlur"
        :data-component-id="componentId || ''"></textarea>
      <input
        v-else
        :type="inputType || 'text'"
        :name="name || componentId || ''"
        :value="value"
        :focus="focus"
        :key="'input-'+componentId"
        :placeholder="placeholder"
        class="zr-field__input zr-cell__bd"
        :class="{ 'zr-field__input--right' : right }"
        placeholder-class="zr-field__placeholder"
        @input="_handleZrFieldChange"
        @focus="_handleZrFieldFocus"
        @blur="_handleZrFieldBlur"
        :data-component-id="componentId || ''"/>
    </div>
</template>

<script>
  import {extractComponentId} from '../../utils/helper'
  export default {
    props: {
      error: Boolean,
      mode: String,
      title: String,
      type: String,
      focus: Boolean,
      name: String,
      componentId: String,
      value: String,
      inputType: String,
      right: Boolean,
      placeholder: String,
      handleZrFieldChange: Function,
      handleZrFieldFocus: Function,
      handleZrFieldBlur: Function
    },
    methods: {
      _handleZrFieldChange (event) {
        const componentId = extractComponentId(event)
        event.componentId = componentId

        // console.info('[zan:field:change]', event)

        if (this.handleZrFieldChange) {
          return this.handleZrFieldChange(event)
        }

        console.warn('页面缺少 handleZrFieldChange 回调函数')
      },

      _handleZrFieldFocus (event) {
        const componentId = extractComponentId(event)
        event.componentId = componentId

        console.info('[zan:field:focus]', event)

        if (this.handleZrFieldFocus) {
          return this.handleZrFieldFocus(event)
        }

        console.warn('页面缺少 handleZrFieldFocus 回调函数')
      },

      _handleZrFieldBlur (event) {
        const componentId = extractComponentId(event)
        event.componentId = componentId

        console.info('[zan:field:blur]', event)

        if (this.handleZrFieldBlur) {
          return this.handleZrFieldBlur(event)
        }

        console.warn('页面缺少 handleZrFieldBlur 回调函数')
      }
    }
  }
</script>

<style scoped>

</style>
