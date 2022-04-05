<template>
  <Wrap :delay='2500'>
    <template #default='data'>
      <div class="color-white gutter_col">
        <div style="min-height: 50px">
          <transition name='slideBottom'> 
            <h2 v-show='data.show[0]' class="title-lg pos-r linear-color text-align-center">Creating new sports betting experiences on Betweb3.0</h2>
          </transition>
        </div>
        
        <transition name='slideBottom'> 
          <div v-show='data.show[2]'>
            <p class="text-align-center mt-32 desc line-height-24">Betweb2.0's online sports betting market is already huge and mature. Nonetheless, with the advent of Betweb3.0, we are starting to see many drawbacks to traditional online sports betting platforms. </p>
            <p class="text-align-center desc line-height-24">Betweb3 creates the cleanest user experience, allowing users to connect their wallet to complete USDT betting and all interactive experience.</p>
          </div>
        </transition>
        
        <div style="height: 34vw" class="bg-gray-20 mt-48 flex items-center justify-center">
          视频
        </div>
      </div>
    </template>
  </Wrap>
</template>

<script>
import { defineComponent, ref } from 'vue'
import Wrap from '@/components/wrap'

export default defineComponent({
  components: {
    Wrap
  },
  props: {},
  setup(props) {}
})
</script>
