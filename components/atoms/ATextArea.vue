<template lang="pug">
  .custom--a-text-area-cnt.relative
    textarea.custom--a-text-area.has-background-grey(
      type="text"
      :name="label"
      :value="value"
      @input="$emit('input', $event.target.value)"
      :class="{ inputted: !!value }"
    )
    .custom--a-text-area-label(
      :class="{ inputted: !!value }"
    ) {{label}}
  </template>

<script>
export default {
  name: 'ATextArea',
  props: {
    value: {
      type: String,
      default: ''
    },
    label: {
      type: String,
      default: 'コメント'
    }
  }
}
</script>

<style lang="scss" scoped>
$textarea-radius: 4px;

.custom--a-text-area-cnt {
  overflow: hidden;
}

.custom--a-text-area {
  // 初期化用
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  outline: none;
  background-color: transparent;

  // ここからがスタイル
  z-index: 10;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  width: 125%;
  min-width: 125%;
  max-width: 125%;
  height: 50px;
  transform: scale(0.8);
  transform-origin: left top;
  padding: 25px 15px 10px;
  color: $text;
  font-size: 16px;
  border: 1px solid transparent;
  border-radius: $textarea-radius;
  transition: all 0.3s;

  &::-webkit-input-placeholder {
    color: $text;
    font-size: 0.8rem;
  }

  &:focus {
    border-color: $primary;
  }

  &:focus,
  &.inputted {
    height: 120px;
  }
}

.custom--a-text-area-label {
  position: absolute;
  top: 8px;
  left: 12px;
  height: 20px;
  white-space: nowrap;
  text-align: left;
  bottom: 0;
  color: $text;
  font-size: 0.9rem;
  transition: 0.3s all;
}

.custom--a-text-area:focus + .custom--a-text-area-label,
.custom--a-text-area-label.inputted {
  transform: scale(0.6);
  transform-origin: left top;
  color: $white-ter;
}

.custom--a-text-area-search {
  position: absolute;
  right: 8px;
  top: 0;
  bottom: 0;
}
</style>
