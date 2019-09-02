<template lang="pug">
  .custom--a-arrow.button.is-rounded(
    :class="{'has-background-white-bis': circle, circle}"
    @click="$emit('click')"
  )
    span.icon.custom--a-arrow-arrow(
      :class="{right, left, up, down}"
    )
      i.material-icons.is-size-6(
        :class="[{'has-text-black': circle}, `has-text-${color}`]"
      )
        template(
          v-if="left"
        ) arrow_back_ios
        template(
          v-else
        ) arrow_forward_ios
</template>

<script>
export default {
  name: 'AArrow',
  props: {
    left: {
      type: Boolean,
      default: false
    },
    right: {
      type: Boolean,
      default: false
    },
    up: {
      type: Boolean,
      default: false
    },
    down: {
      type: Boolean,
      default: false
    },
    color: {
      type: String,
      default: 'white'
    },
    circle: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss" scoped>
.custom--a-arrow {
  width: 32px !important;
  height: 32px !important;
  border: none !important;
  background-color: transparent;
  box-shadow: none;

  &.circle {
    box-shadow: 0 0 6px 3px rgba(0, 0, 0, 0.1);
  }
}

.custom--a-arrow-arrow {
  &.left {
    padding-left: 6px;
  }

  &.right {
    padding-left: 2px;
  }

  &.up {
    transform: rotate(-90deg);
  }

  &.down {
    transform: rotate(90deg);
  }
}
</style>
