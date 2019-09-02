<template lang="pug">
  .flex.align-center.justify-center.p-left-24.p-right-12.custom--a-flag(
    :class="[{ small }, `${color}`]"
    :style="topStyle"
  )
    .tag.has-text-weight-semibold.custom--a-flag-tag(
      :class="[{ small },`is-${color}`, `${color}`]"
      :style="topStyle"
    )
      slot
    .custom--a-flag-triangle1(
      :class="[`${color}`]"
      :style="triangle1Style"
    )
    .custom--a-flag-triangle2(
      :class="[`${color}`]"
      :style="triangle2Style"
    )
</template>

<script>
export default {
  name: 'AFlag',
  props: {
    color: {
      type: String,
      default: 'primary'
    },
    small: {
      type: Boolean,
      default: false
    },
    colorCode: {
      type: String,
      default: null
    }
  },
  computed: {
    topStyle() {
      if (!this.colorCode) {
        return null
      }
      return {
        backgroundColor: this.colorCode,
        color: `white`
      }
    },
    triangle1Style() {
      if (!this.colorCode) {
        return
      }
      return {
        borderColor: `${this.colorCode} transparent transparent transparent`
      }
    },
    triangle2Style() {
      if (!this.colorCode) {
        return
      }
      return {
        borderColor: `transparent transparent transparent ${this.colorCode}`
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.tag:not(body).is-primary {
  &.small {
    font-size: 0.5em;
    padding-left: 1em;
    margin-left: -8px;
  }
}

.custom--a-flag {
  position: relative;
  height: 24px;
  max-height: 24px;
  display: table;

  &.small {
    position: relative;
    height: 16px;
    max-height: 16px;
    display: table;
  }

  &.primary {
    background-color: $primary;
  }

  &.danger {
    background-color: $danger;
  }

  &.info {
    background-color: $info;
  }

  &.success {
    background-color: $success;
  }
}

.custom--a-flag-tag {
  line-height: 24px;
  height: 24px;
  padding: 0 !important;
  display: block !important;

  &.small {
    line-height: 16px;
    height: 16px;
    padding: 0 !important;
    display: block !important;
  }
}

.custom--a-flag-triangle1 {
  position: absolute;
  top: 0;
  right: -8px;
  height: 0;
  width: 0;
  border-style: solid;
  border-width: 12px 8px 0 0;

  &.primary {
    border-color: $primary transparent transparent transparent;
  }

  &.danger {
    border-color: $danger transparent transparent transparent;
  }

  &.info {
    border-color: $info transparent transparent transparent;
  }

  &.success {
    border-color: $success transparent transparent transparent;
  }
}

.custom--a-flag-triangle2 {
  position: absolute;
  bottom: 0;
  right: -8px;
  height: 0;
  width: 0;
  border-style: solid;
  border-width: 12px 0 0 8px;

  &.primary {
    border-color: transparent transparent transparent $primary;
  }

  &.danger {
    border-color: transparent transparent transparent $danger;
  }

  &.info {
    border-color: transparent transparent transparent $info;
  }

  &.success {
    border-color: transparent transparent transparent $success;
  }
}
</style>
