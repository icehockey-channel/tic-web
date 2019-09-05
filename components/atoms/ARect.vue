<template lang="pug">
  component(
    :is="to ? 'nuxt-link' : 'div'"
    :to="to"
  )
    .custom--a-rect(
      :class="{ border, pointer, 'top-border': topBorder }"
    )
      .custom--a-rect-color.colored(
        v-if="gradation"
        :class="{ gradation }"
        :style="{ opacity }"
      )
      .custom--a-rect-color(
        v-else-if="!transparent"
        :class="[{ colored }, `has-background-${color}`]"
        :style="{ opacity }"
      )
      .custom--a-rect-slot
        slot
</template>

<script>
export default {
  name: 'ARect',
  props: {
    to: {
      type: String,
      default: null
    },
    border: {
      type: Boolean,
      default: false
    },
    topBorder: {
      type: Boolean,
      default: false
    },
    color: {
      type: String,
      default: 'black-bis'
    },
    pointer: {
      type: Boolean,
      default: false
    },
    gradation: {
      type: Boolean,
      default: false
    },
    transparent: {
      type: Boolean,
      default: false
    },
    opacity: {
      type: Number,
      default: 1
    }
  },
  computed: {
    colored () {
      return this.color !== 'black-bis'
    }
  }
}
</script>

<style lang="scss" scoped>
.custom--a-rect {
 // color: $text;
  position: relative;

  &.border {
    border-bottom: grey 1px solid;
  }

  &.top-border {
    border-top: grey 1px solid;
  }

  &.pointer {
    cursor: pointer;
  }
}

.custom--a-rect-color {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  width: 0;
  transition: all 0.3s;

  &.colored {
    width: 100%;
  }

  &.gradation {
    background: linear-gradient(
      135deg,
      #5b646e 0,
      #4e565f 10%,
      #22282e 20%,
      #12181d 40%,
      #090e13 45%,
      #080d12 50%
    );
  }
}

.custom--a-rect-slot {
  position: relative;
  background-color: transparent;
}
</style>
