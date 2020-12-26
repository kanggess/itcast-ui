<template>
  <div class="hm-radio-group">
      <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'HmRedioGroup',
  provide () {
    // foo: 'bar'
    return {
      RadioGroup: this
    }
  },
  props: {
    // hm-radio-group接收到了value值
    value: null
  }
}
</script>

<style>

</style>
