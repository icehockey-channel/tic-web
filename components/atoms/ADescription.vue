<template lang="pug">
.custom--a-description(
  :class="[{ 'has-text-left': !center,
  'has-text-centered': center,
  'has-text-weight-medium': !bold ,
  'has-text-weight-semibold': bold },
  `has-text-${color}`]"
  :style="{width: `${width}px`}"
)
  slot
</template>

<script>
export default {
  name: 'ADescription',
  props: {
    color: {
      type: String,
      default: 'white-bis'
    },
    center: {
      type: Boolean,
      default: false
    },
    bold: {
      type: Boolean,
      default: false
    },
    width: {
      type: Number,
      default: null
    }
  }
}
</script>

<style lang="scss">
.custom--a-description {
  font-size: 0.75rem;
  line-height: 1.8;
  letter-spacing: -0.02rem;
}
</style>
