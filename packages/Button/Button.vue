
<template>
  <button class="t-button" @click="$emit('click', $event)" :style="style" :class="classes">
    <slot></slot>
  </button>
</template>

<script >
import { defineComponent,computed } from 'vue'
export default defineComponent({
  name: 'TButton',
  props: {
    color: {
      type: String
    },
    round: {
      type: Boolean,
      default: false
    },
    type: {
      type: String,
      default: 'default'
    },
    size: {
      type: String,
      default: 'default'
    },
    circle: {
      type: Boolean,
      default: false
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  emits: ['click'],
  setup(props){
    const {color,round,type,size,circle,disabled} = props
    const classes = computed(() => {
      return {
        [`t-type-${type}`]: type,
        [`t-button-${size}`]: size,
        [`is-round`]: round,
        [`is-circle`]: circle,
        [`is-disabled`]: disabled,
      };
    });
    return {
      // 用户自定义样式
      style: {
        background: color,
      },
      classes

    }
  }
})
</script>

<style lang="less">
@import './style/Button.less';
</style>
