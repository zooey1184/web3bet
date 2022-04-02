<template>
  <div>
    <div class=" text-align-center">Web3bet 正在拓展以将体育投注体验带到多有兼容的网络</div>
    <div class="flex justify-center">
      <div class="title-lg linear-color">多链技术和拓展</div>
    </div>
  </div>

  <div class="flex justify-center">
    <Circle />
  </div>
</template>

<script>
import { defineComponent, ref } from 'vue'
import Circle from '../../components/circle'

export default defineComponent({
  components: {
    Circle
  },
  props: {},
  setup(props) {}
})
</script>