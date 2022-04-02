<template>
  <div class="color-white bg">
    <Navbar :isMobile='isMobile' />
    <div class='bg gutter_x' style="margin-top: 60px;" ref='productRef'>
      <Part1 />
    </div>
    <div class='bg' ref='tokenRef'>
      <div class="gutter_x">
        <Part2 />
        <Part3 />
        <Part4 />
        <Part5 />
        <Part6 />
      </div>
      <div style='padding: 0 3%; margin-top: -4vh; box-sizing: border-box'>
        <img src="./assets/filter-line.png" class="w-100p" alt="">
      </div>
      
      
      <div class="gutter_x">
        <Part7 />
        <Part8 />
      </div>
    </div>
    <div class='bg' ref='mapRef'></div>
    <div class="bg" style="padding: 4vw 10vw">
      <Footer />
    </div>
  </div>
</template>

<script>
import { defineComponent, ref, onMounted, provide } from 'vue'
import Circle from './components/circle'
import Navbar from './components/nav'
import Steps from './components/steps'
import MSteps from './components/steps/m-index.vue'
import LinearBox from './components/linear-box'
import Part1 from './views/part1'
import Part2 from './views/part2'
import Part3 from './views/part3'
import Part4 from './views/part4'
import Part5 from './views/part5'
import Part6 from './views/part6'
import Part7 from './views/part7'
import Part8 from './views/part8'

import Footer from './views/footer-pane'

const MOBILE_WIDTH = 1024
export default defineComponent({
  components: {
    Circle,
    Navbar,
    Steps,
    MSteps,
    LinearBox,
    Part1,
    Part2,
    Part3,
    Part4,
    Part5,
    Part6,
    Part7,
    Part8,
    Footer
  },
  props: {},
  setup(props) {
    const isMobile = ref()
    const productRef = ref()
    const tokenRef = ref()
    const mapRef = ref()

    provide('isMobile', isMobile)

    const throttleFn = (fn, wait) => {
      let timer = null;
      let timeStamp = +new Date()
      return function () {
        if (+new Date() - timeStamp > wait) {
          timeStamp = + new Date()
          timer = setTimeout(() => {
            fn()
          }, wait)
        }
      }
    }
    window.onscroll = throttleFn((e) => {
      const product = productRef.value?.getBoundingClientRect()
      const token = tokenRef.value?.getBoundingClientRect()
      if(product) {
        if (product.y + product.height > 80 &&  product.y + product.height <= product.height) {
          console.log('product');
        }
        if (token.y + token.height > 80 &&  token.y + token.height <= token.height) {
          console.log('token');
        }
      }
    }, 200)

    window.onresize = (e) => {
      if (window.innerWidth <= MOBILE_WIDTH) {
        isMobile.value = true
      } else {
        isMobile.value = false
      }
    }
    onMounted(() => {
      if(window.innerWidth <= MOBILE_WIDTH) {
        isMobile.value = true
      }
    })

    return {
      productRef,
      tokenRef,
      mapRef,
      isMobile
    }
  }
})
</script>