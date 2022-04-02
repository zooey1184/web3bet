<template>
  <div class="flex" ref='container'>
    <div class="line">
    <div class="bar" :style="{left: state.left + 'px', width: state.width + 'px'}"></div>
    <div class="flex items-center">
      <div class="item" :ref='refMap[item.value]' @click='handlePickItem(item, index)' v-for='(item, index) in options'>{{item.label}}</div>
    </div>
  </div>
  </div>
</template>


<script>
import { computed, defineComponent, nextTick, onMounted, reactive, ref, watch, watchEffect } from 'vue'

export default defineComponent({
  components: {},
  props: {
    options: {
      type: Array,
      default: ()=> ([
        {
          label: 'CREATE',
          value: 'create',
          desc: 'Choose your champions and create your portfolio',
        },
        {
          label: 'EDIT',
          value: 'edit',
          desc: 'Improve your strategy and change your mind at any',
        },
        {
          label: 'CREATE',
          value: 'map',
          desc: 'Choose your champions and create your portfolio',
        },
        {
          label: 'EDIT',
          value: 'token',
          desc: 'Improve your strategy and change your mind at any',
        }
      ])
    },
    active: {
      type: Number,
      default: 0
    }
  },
  setup(props) {
    const state = reactive({
      active: props.active,
      left: 16,
      width: 55
    })
    const container = ref()

    const rect = reactive({})
    const refMap = computed(() => {
      const m = {}
      props.options.forEach(item => {
        m[item.value] = ref()
      });
      return m
    })

    const handlePickItem = (item, index) => {
      const _contaier = container.value
      const rect = _contaier.getBoundingClientRect()
      const _item = refMap.value[item.value].value[0]
      const _itemR = _item.getBoundingClientRect()
      const _left = _itemR.x - rect.x
      state.width = _itemR.width
      
      state.left = _left
    }

    
    onMounted(() => {
      
      
    })

    return {
      state,
      refMap,
      container,
      handlePickItem
    }
  }
})
</script>

<style lang="less" scoped>
.line {
  position: relative;
  padding: 16px;
  border-top: 1px solid #fff;
}
.bar {
  height: 6px;
  position: absolute;
  left: 16px;
  top: -3px;
  width: 20px;
  background: rgb(0, 225, 255);
  transition: all 200ms linear;
}
.item {
  margin-right: 20px;
  &:last-child {
    margin-right: 0;
  }
}
</style>