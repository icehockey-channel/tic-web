<template lang="pug">
  component.custom--a-button.button.has-text-weight-semibold(
    :is="componentName"
    :to="to || undefined"
    :href="href || undefined"
    :target="href ? '_blank' : undefined"
    :disabled="disabled"
    :class="[{ fluid, small, transparent }, `is-${color}`]"
    @click="click"
  )
    slot
</template>

<script>
export default {
  name: 'AButton',
  props: {
    color: {
      type: String,
      default: 'primary'
    },
    fluid: {
      type: Boolean,
      default: false
    },
    small: {
      type: Boolean,
      default: false
    },
    transparent: {
      type: Boolean,
      default: false
    },
    to: {
      type: [String, Object],
      default: ''
    },
    href: {
      type: String,
      default: ''
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    componentName () {
      if (!this.disabled && !!this.to) {
        return 'nuxt-link'
      }
      if (this.href) {
        return 'a'
      }
      return 'div'
    }
  },
  methods: {
    click () {
      if (!this.disabled) {
        this.$emit('click')
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.custom--a-button {
  height: 40px;
  padding: 8px 16px !important;
  font-size: 0.9rem;
  transition: all 0.3s;

  // initial variablesは書いてあげないといけないらしい。
  &.is-grey {
    border: none;
    background-color: grey;
    color: white;
  }

  &.fluid {
    width: 100%;
  }

  &.small {
    height: 32px;
    font-size: 0.75rem;
    padding: 6px 12px !important;
  }

  &.transparent {
    background-color: transparent !important;
    color: primary;
  }
}
</style>
