<template lang="pug">
  span.tag.has-text-weight-bold.custom--a-label(
    :class="[ `is-${color}` ]"
  )
    slot
</template>

<script>
export default {
  name: 'ALabel',
  props: {
    color: {
      type: String,
      default: 'danger'
    }
  }
}
</script>

<style lang="scss">
.custom--a-label {
  border-radius: 2px !important;
  line-height: 1.25rem !important;
  height: 1.25rem !important;
  font-size: 0.6rem !important;
}
</style>
