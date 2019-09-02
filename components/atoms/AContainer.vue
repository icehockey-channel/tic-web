<template lang="pug">
  .custom--a-container(
    :class="{ 'p-top-0': noPadding, 'p-bottom-0': noPadding }"
  )
    slot
</template>

<script>
export default {
  name: 'AContainer',
  props: {
    noPadding: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss" scoped>
.custom--a-container {
  padding: 20px;
}
</style>
