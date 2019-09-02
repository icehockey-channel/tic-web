<template lang="pug">
  .flex.justify-center.custom--a-main-cnt
    .custom--a-main.is-desktop(
      :class="{ 'not-full': notFullHeight, transparent }"
    )
      .custom--a-main-wrapper
        slot
</template>

<script>
export default {
  name: 'AMain',
  props: {
    notFullHeight: {
      type: Boolean,
      default: false
    },
    transparent: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss">
.custom--a-main {
  width: 100vw;
  max-width: 640px;

  @media screen and (min-width: 960px) {
    max-width: 960px;
  }

  &.not-full {
    min-height: 0 !important;
  }

  &.transparent {
    background-color: transparent;
  }
}

.custom--a-main-wrapper {
  width: 100%;
}
</style>
