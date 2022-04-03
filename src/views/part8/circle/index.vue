<template>
  <div class="pos-r" @click="handleClick">
    <div class="circle bg z-index-9" :style="{width: getSize, height: getSize}">
      <img class="w-100p" v-if='!solid' src="../../../assets/circle-dashed.png" alt="">
      <img class="w-100p active" v-else src="../../../assets/circled.png" alt="">
      <div class="content">
        <slot></slot>
      </div>
    </div>
    <div class="dashed pos-a " :style="{transform: `rotateZ(${rotate}deg)`, width: getSize,}" v-if='showLine'>
      <svg xmlns="http://www.w3.org/2000/svg" version="1.1">
      <defs>
        <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
          <stop offset="0%" style="stop-color:#13DCDD; stop-opacity:1" />
          <stop offset="50%" style="stop-color:#FA87CA; stop-opacity:1" />
          <stop offset="100%" style="stop-color:#FFD58A;stop-opacity:1" />
        </linearGradient>
      </defs>
        <g fill="none">
          <path stroke="url(#grad1)" stroke-width="3" stroke-dasharray="5,5" :d="`M0 0 l${lineSize} 1`" />
        </g>
      </svg>
    </div>
  </div>
  
</template>

<script>
import { computed, defineComponent, ref } from 'vue'

export default defineComponent({
  components: {},
  props: {
    solid: {
      type: Boolean,
    },
    size: {
      type: [String, Number],
      default: '164'
    },
    lineSize: {
      type: Number,
      default: 200
    },
    rotate: {
      type: Number,
      default: 50
    },
    showLine: {
      type: Boolean,
      default: true
    }
  },
  emits: ['click'],
  setup(props, {emit}) {
    const getSize = computed(() => {
      const s = props.size
      if (typeof s === 'number') {
        return `${s}px`
      } else if (typeof s === 'string') {
        if (s.match(/[px,rem,em,vw,vh]$/)) {
          return s
        } else {
          return `${s}px`
        }
      }
    })
    const handleClick = () => {
      emit('click')
    }
    return {
      getSize,
      handleClick
    }
  }
})
</script>

<style lang="less" scoped>
.circle {
  position: relative;
  border-radius: 10000px;
}
.dashed {
  height: 1px;
  top: 49%;
  left: 50%;
  overflow: hidden;
  transform-origin: left top;
  transition: all 300ms linear;
}
.content {
  position: absolute;
  width: 94%;
  left: 3%;
  top: 3%;
  height: 94%;
}
.active {
  box-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
  border-radius: 1000px;
}
</style>