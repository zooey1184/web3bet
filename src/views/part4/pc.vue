<template>
  <Wrap>
    <template #default='data'>
      <div class="flex gutter_col justify-between">
      
        <div class="color-white" style='width: 42%'>
          <transition name='slideBottom'>
            <div v-show='data.show[0]' style="margin-bottom: 36px" class="linear-color title-lg">The core process of smart contract execution</div>
          </transition>
          
          <transition name='slideBottom'>
            <div v-show='data.show[1]' style="margin-bottom: 29px" class="grey">
              <div>The decentralization of the workflow, from user betting, user compensation and other links to achieve decentralization; The event data results in-depth cooperation with Sportradar Group AG (NASDAQ: SRAD) and data delivery through Chainlink"</div>
            </div>
          </transition>
          <transition name='slideBottom'>
            <div v-show='data.show[2]' class="my-16 color-blue" style="margin-bottom: 53px">Decentralization is the first premise of the project</div>
          </transition>

          <transition name='slideBottom'>
            <div class="item" v-show='data.show[3]'>
              <div><img src="../../assets/part4-1.png" alt=""></div>
              <p style='margin-left: 13px'>Fair</p>
            </div>
          </transition>
          <transition name='slideBottom'>
            <div class="item" v-show='data.show[4]'>
              <div><img src="../../assets/part4-2.png" alt=""></div>
              <p style='margin-left: 13px'>Impartial</p>
            </div>
          </transition>
          <transition name='slideBottom'>
            <div class="flex items-center" v-show='data.show[5]'>
              <div><img src="../../assets/part4-3.png" alt=""></div>
              <p style='margin-left: 13px'>Transparent</p>
            </div>
          </transition>
        </div>
        <div style="height: 16.5vw; width: 24vw">
          <img src="../../assets/part4_gif.gif" class="w-100p" alt="">
          </div>
      </div>
    </template>
  </Wrap>
</template>

<script>
import { defineComponent, ref } from 'vue'
import Wrap from '@/components/wrap'
import MouseTrack from '@/components/mouse-track'

export default defineComponent({
  components: {
    Wrap,
    MouseTrack
  },
  props: {},
  setup(props) {

  }
})
</script>

<style lang="less" scoped>
.item {
  display: flex;
  align-items: center;
  margin-bottom: 37px;
}
</style>