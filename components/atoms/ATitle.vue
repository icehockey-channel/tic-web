<template lang="pug">
  .custom--a-title.has-text-weight-semibold.m-bottom-8(
    :class="[{ 'has-text-left': !center, 'has-text-centered': center }, `has-text-${color}`]"
  )
    slot
</template>

<script>
export default {
  name: 'ATitle',
  props: {
    color: {
      type: String,
      default: 'white-bis'
    },
    center: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss" scoped>
.custom--a-title {
  font-size: 1.25rem;
  letter-spacing: -0.03rem;
}
</style>
