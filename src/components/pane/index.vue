<template>
  <div ref="wrapRef">
    <slot v-bind='state.rect'></slot>
  </div>
</template>

<script>
import { defineComponent, onMounted, reactive, ref } from 'vue'

export default defineComponent({
  components: {},
  props: {},
  setup(props) {
    const wrapRef = ref()
    const state = reactive({
      rect: {}
    })

    onMounted(() => {
      const r = wrapRef.value
      if (r) {
        const rect = r.getBoundingClientRect()
        console.log(rect);
        state.rect = rect
      }
    })

    return {
      wrapRef,
      state
    }
  }
})
</script>