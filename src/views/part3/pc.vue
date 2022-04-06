<template>
  <Wrap>
    <template #default='data'>
      <div class="pos-r">
        <!-- <img src="../../assets/part3-bg.png" class="pos-a" style="left: -8vw; top: -12vw; z-index: 9" alt=""> -->
        <div class="flex gutter_col justify-between">
          <!-- <div style="height: 16.5vw; width: 24vw" class="bg-gray-30 flex-0 mr-24 mt-16">
          </div> -->
          <img style="width: 24vw; height: 16.5vw; z-index: 2" src="../../assets/part3-gif.gif" alt="">
          <div class="color-white">
            <transition name='slideBottom'>
              <div v-show='data.show[0]' class="linear-color title-lg" style="margin-bottom: 4px">The first Betweb3 sports betting platform</div>
            </transition>
            <transition name='slideBottom'>
              <div v-show='data.show[1]' class="subTitle font-weight-600 mt-48 mb-32">USDT decentralized capital pool</div>
            </transition>
            
            <transition name='slideBottom'>
              <div v-show='data.show[2]' class="grey" style="margin-top: 6px; margin-bottom: 55px">
                <div >The essence of the traditional sports betting platform is that the platform itself endorses the platform itself to make payment for the user's wins and losses. </div>
                <div>Betweb3 adopts the concept of decentralization and builds a completely decentralized capital pool to undertake the user's payment problem.</div>
              </div>
            </transition>
      

            <transition name='slideBottom'>
              <div class="item" v-show='data.show[3]'>
                <div>
                  <img src="../../assets/part3-1.png" alt="">
                </div>
                <p style='margin-left: 13px'>Destruction of the ownership of the capital pool</p>
              </div>
            </transition>
            <transition name='slideBottom'>
              <div class="item" v-show='data.show[4]'>
                <div>
                  <img src="../../assets/part3-2.png" alt="">
                </div>
                <p style='margin-left: 13px'>60% of each profit is distributed to token holders, 10% is automatically repurchased destroyed token, and 30% remains in the capital pool</p>
              </div>
            </transition>
            <transition name='slideBottom'>
              <div class="flex items-center" v-show='data.show[5]'>
                <div><img src="../../assets/part3-3.png" alt=""></div>
                <p style='margin-left: 13px'>Amount and profit are completely transparent</p>
              </div>
            </transition>
          </div>
        </div>
      </div>
    </template>
  </Wrap>
</template>

<script>
import { defineComponent, inject, ref, watch } from 'vue'
import Wrap from '@/components/wrap'
import MouseTrack from '@/components/mouse-track'

export default defineComponent({
  components: {
    Wrap,
    MouseTrack,
  },
  props: {},
  setup(props) {

    return {
      
    }
  }
})
</script>

<style lang="less" scoped>
.item {
  margin-bottom: 37px;
  display: flex;
  align-items: center;
}
</style>