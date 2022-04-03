<template>
  <div v-if='isMobile'>
    <div class="m_nav bg flex items-center justify-between">
      <More v-model:value='state.visible' />
      <div class="color-white">
        Logo
      </div>
      <div>
        
      </div>
    </div>
    <transition name='slide'>
      <div v-if='state.visible' class="m_nav_content">

      </div>
    </transition>
  </div>

  <div v-else class="pc_nav bg">
    <div class="flex items-center">
      <div>
        <!-- <div class="linear-bg" style="height: 43px">
          <img style="height: 43px" src='../../assets/logo-black.png'/>
        </div> -->
        <img style="height: 43px" src='../../assets/logo.png'/>
      </div>
      <div class="flex items-ceneter justify-between ml-40">
        <div class="ml-40 inline-block" @click="handleClickMenuItem(item.value)" :class="{'primary': state.active === item.value}" v-for='item in options'>{{item.label}}</div>
      </div>
    </div>
    <div class="flex items-center">
      <LinearBox v-for='item in btnList' class=" ml-24">
        <div class="primary pc_btn_px ">{{item.label}}</div>
      </LinearBox>
      <div class="linear-bg ml-24 pc_btn_px" style="border-radius: 2px">{{launch}}</div>
    </div>
  </div>
</template>

<script>
import { defineComponent, onMounted, reactive, ref, watch } from 'vue'
import More from './more-icon.vue'
import LinearBox from '../linear-box'

export default defineComponent({
  components: {
    More,
    LinearBox
  },
  props: {
    options: {
      type: Array,
      default: () => ([
        {
          label: 'Product',
          value: 'product'
        },
        {
          label: 'Token economy',
          value: 'token'
        },
        {
          label: 'Road Map',
          value: 'map'
        }
      ])
    },
    active: {
      type: String,
      default: 'product'
    },
    btnList: {
      type: Array,
      default: () => ([
        {
          label: 'Pledge Of Shares',
          value: 'pledge'
        },
        {
          label: 'Docs',
          value: 'doc'
        },
      ]),
      
    },
    launch: {
      type: String,
      default: 'Launch App'
    },
    isMobile: Boolean
  },
  emits: ['change', 'update:active'],
  setup(props, {emit, expose}) {
    const isMobile = ref(false)
    const state = reactive({
      visible: false,
      active: props.active
    })
    watch(() => props.active, (n) => {
      state.active = n
    })
    watch(() => state.active, (n) => {
      emit('update:active', n)
    })

    const handleClickMenuItem = (item) => {
      emit('change', item)
      emit('update:active', item)
    }
    
    return {
      state,
      handleClickMenuItem
    }
  }
})
</script>

<style lang="less" scoped>
@height: 60px;
@h-lg: 80px;
@h-md: 70px;
.m__nav {
  position: fixed;
  width: 100%;
  left: 0;
  top: 0;
}
.m_nav {
 .m__nav;
 z-index: 99;
 height: @height;
}
.m_nav_content {
  height: 100%;
  z-index: 89;
  .m__nav;
}
.slide-enter-active, .slide-leave-active {
  transition: all .5s ease;
}

.slide-enter-from, .slide-leave-to {
  opacity: 0;
  transform: translateY(-200px);
}
.pc_nav {
  height: @height;
  position: fixed;
  top: 0;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  color: #fff;
  box-sizing: border-box;
  padding: 0 30px;
  z-index: 89;
  @media (min-width: 1040px) and (max-width: 1560px) {
    height: @h-md;
  }
  @media (min-width: 1561px) {
    height: @h-lg;
  }
}
.pc_btn_px {
  width: 125px;
  height: 38px;
  display: flex;
  align-items: center;
  justify-content: center;
  @media (min-width: 1040px) and (max-width: 1560px) {
    width: 145px;
    height: 42px;
  }
  @media (min-width: 1561px) {
    width: 175px;
    height: 47px;
  }
}
</style>