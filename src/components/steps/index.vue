<template>
  <div v-if='align==="left"'>
    <Arrow dir='up' :disabled="state.active===0" />
    <div class="line">
      <div class="bar" :style="{top: (40*state.active+24)+'px'}"></div>
      <div v-for='(item, index) in options' @click="state.active = index" class="item">
        <div>{{item.label}}</div>
        <div class="desc" :class="{desc_act: state.active === index}">{{item.desc}}</div>
      </div>
    </div>
    <Arrow dir='down' :disabled="state.active===options.length-1" />
  </div>

  <div v-else>
    <div class="flex justify-end">
      <Arrow dir='up' @click="handleClickUp" :disabled="state.active===0" />
    </div>
    <div class="line_right">
      <div class="bar_right" :style="{top: (50*state.active+16)+'px'}"></div>
      <div v-for='(item, index) in options' @click="state.active = index" class="item text-align-right">
        <div class="subTitle" :class="{'color-blue': state.active === index}">{{item.label}}</div>
        <div class="desc" v-if='item.desc' :style="{maxHeight: state.active === index ? item.maxHeight || '120px' : '0'}">
          <slot :name='item.slot'>
            <template v-if='typeof item.desc === "string"'>
              <div class="desc_item">{{item.desc}}</div>
            </template>
            <template v-if='typeof item.desc === "object"'>
              <div v-for='ii in item.desc' class="desc_item">{{ii}}</div>
            </template>
          </slot>
        </div>
      </div>
    </div>
    <div class="flex justify-end">
      <Arrow dir='down' @click='handleClickDown' :disabled="state.active===options.length-1" />
    </div>
  </div>
</template>

<script>
import { defineComponent, reactive, ref } from 'vue'
import Arrow from './arrow.vue'

export default defineComponent({
  components: {
    Arrow
  },
  props: {
    options: {
      type: Array,
      default: ()=> ([])
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

    const handleClickDown = () => {
      if (state.active < props.options.length - 1) {
        state.active++
      }
    }
    const handleClickUp = () => {
      if (state.active > 0) {
        state.active--
      }
    }


    return {
      state,
      handleClickDown,
      handleClickUp
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
  padding-right: 32px;
  margin: 16px 30px;
  transition: all 100ms linear;
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
  width: 10px;
  height: 24px;
  background: #3098fe;
  right: -5px;
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
  max-height: 20px;
}
.desc_item {
  position: relative;
  padding-right: 18px;
  &:after {
    content: "";
    position: absolute;
    width: 7px;
    height: 7px;
    border-radius: 7px;
    background: #fff;
    top: 8px;
    right: 0;
  }
}
</style>