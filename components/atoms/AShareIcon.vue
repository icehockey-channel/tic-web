<template lang="pug">
  .custom--a-share-icon.flex.align-center.justify-center(
    :class="{ twitter, facebook }"
  )
    span.icon
      i.fab.fa-twitter(
        v-if="twitter"
      )
      i.fab.fa-lg.fa-facebook-f(
        v-else-if="facebook"
      )
      i.fas.fa-lg.fa-link(
        v-else-if="link"
      )
</template>

<script>
export default {
  name: 'AShareIcon',
  props: {
    twitter: {
      type: Boolean,
      default: false
    },
    facebook: {
      type: Boolean,
      default: false
    },
    link: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss" scoped>
.custom--a-share-icon {
  width: 40px;
  height: 40px;
  border-radius: 4px;

  &.twitter {
    background-color: $twitter;
  }

  &.facebook {
    background-color: $facebook;
  }
}
</style>
