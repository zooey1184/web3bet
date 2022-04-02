<template>
  <div class="flex justify-between gutter_col">
    <div style="height: 16.5vw; width: 30vw">
      <img class="w-100p" src="../../assets/part7.png" alt="">
    </div>
    <div>
      <div class="title-lg linear-color inline-block">代币经济学 多链技术和拓展</div>
      <div class="mt-8 subTitle">Web3bet 正在扩展以将体育投注体验带到所有兼容的网络  Tokenomics</div>
      <div class="flex mt-24">
        <div class="w-25p">
          <div class="gray-9d desc">Token Name</div>
          <div class="desc">Web3bet Token</div>
        </div>
        <div class="w-25p">
          <div class="gray-9d desc">Token ticker</div>
          <div class="desc">BET</div>
        </div>
        <div class="w-25p">
          <div class="gray-9d desc">Token type</div>
          <div class="desc">ERC-20</div>
        </div>
        <div class="w-25p">
          <div class="gray-9d desc">Token supply</div>
          <div class="desc">1,000,000,000</div>
        </div>
      </div>

      <div class="flex mt-40">
        <div class="w-50p flex items-center">
          <div>
            <img src="../../assets/part7-1.png" alt="">
          </div>
          <div class="ml-16">
            <div class="gray">治理</div>
            <div>持有BET代币以获得协议的投票权</div>
          </div>
        </div>
        <div class="w-50p flex items-center">
          <div>
            <img src="../../assets/part7-2.png" alt="">
          </div>
          <div class="ml-16">
            <div class="gray">治理</div>
            <div>持有BET代币以获得协议的投票权</div>
          </div>
        </div>
      </div>

      <div class="flex mt-48">
        <LinearBox>
          <div class="primary font-size-14 px-48 py-8">更多信息</div>
        </LinearBox>
      </div>
    </div>
  </div>
</template>

<script>
import { defineComponent, ref } from 'vue'
import LinearBox from '../../components/linear-box'

export default defineComponent({
  components: {
    LinearBox
  },
  props: {},
  setup(props) {}
})
</script>
