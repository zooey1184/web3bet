<template>
  <div v-if='align==="left"'>
    <div class="circle flex items-center justify-center">上</div>
    <div class="line">
      <div class="bar" :style="{top: (40*state.active+16)+'px'}"></div>
      <div v-for='(item, index) in options' @click="state.active = index" class="item">
        <div>{{item.label}}</div>
        <div class="desc" :class="{desc_act: state.active === index}">{{item.desc}}</div>
      </div>
    </div>
    <div class="circle flex items-center justify-center">下</div>
  </div>

  <div v-else>
    <div class="flex justify-end">
      <div class="circle flex items-center justify-center">上</div>
    </div>
    <div class="line_right">
      <div class="bar_right" :style="{top: (40*state.active+16)+'px'}"></div>
      <div v-for='(item, index) in options' @click="state.active = index" class="item text-align-right">
        <div>{{item.label}}</div>
        <div class="desc" :class="{desc_act: state.active === index}">{{item.desc}}</div>
      </div>
    </div>
    <div class="flex justify-end">
      <div class="circle flex items-center justify-center">下</div>
    </div>
  </div>
</template>

<script>
import { defineComponent, reactive, ref } from 'vue'

export default defineComponent({
  components: {},
  props: {
    options: {
      type: Array,
      default: ()=> ([
        {
          label: 'CREATE',
          desc: 'Choose your champions and create your portfolio',
        },
        {
          label: 'EDIT',
          desc: 'Improve your strategy and change your mind at any',
        },
        {
          label: 'CREATE',
          desc: 'Choose your champions and create your portfolio',
        },
        {
          label: 'EDIT',
          desc: 'Improve your strategy and change your mind at any',
        }
      ])
    },
    active: {
      type: Number,
      default: 0
    },
    align: {
      type: String,
      default: 'right'
    }
  },
  setup(props) {
    const state = reactive({
      active: props.active
    })

    return {
      state
    }
  }
})
</script>

<style lang="less" scoped>
.circle {
  position: relative;
  width: 50px;
  height: 50px;
  border-radius: 50px;
  border: 2px solid #1890ff;
}
.line {
  position: relative;
  border-left: 1px solid #606f8a;
  padding: 16px 0;
  padding-left: 12px;
  margin: 10px 0;
}
.line_right {
  position: relative;
  border-right: 1px solid #606f8a;
  padding: 16px 0;
  padding-right: 12px;
  margin: 16px 24px;
}
.bar {
  position: absolute;
  width: 6px;
  height: 20px;
  background: #3098fe;
  left: -3px;
  top: 16px;
  transition: all 300ms linear;
}
.bar_right {
  position: absolute;
  width: 6px;
  height: 20px;
  background: #3098fe;
  right: -3px;
  top: 16px;
  transition: all 300ms linear;
}
.item {
  margin-bottom: 20px;
  &:last-child {
    margin-bottom: 0;
  }
}
.desc {
  max-height: 0;
  transition: all 150ms linear;
  overflow: hidden;
}
.desc_act {
  max-height: 16px;
}
</style>