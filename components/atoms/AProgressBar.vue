<template lang="pug">
.custom--a-progress-bar
  .custom--a-progress-bar-partial.has-background-grey(
    :style="{ width: `${100 * partial2 / total}%` }"
  )
  .custom--a-progress-bar-partial(
    :style="{ width: `${100 * partial1 / total}%` }"
    :class="{'has-background-danger': error, 'has-background-success': !error}"
  )
</template>

<script>
export default {
  name: 'AProgressBar',
  props: {
    total: {
      type: Number,
      default: 100
    },
    partial1: {
      type: Number,
      default: 30
    },
    partial2: {
      type: Number,
      default: 50
    },
    error: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss" scoped>
.custom--a-progress-bar {
  border-radius: 6px;
  height: 12px;
  background-color: $black-bis;
  position: relative;
  overflow: hidden;
  border: 1px solid $white-bis;
  transition: all 0.3s;
}

.custom--a-progress-bar-partial {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  transition: all 0.3s;
}
</style>
