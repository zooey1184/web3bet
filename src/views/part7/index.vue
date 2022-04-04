<template>

  <div class="flex justify-between gutter_col">
    <div style="height: 16.5vw; width: 30vw;" class="pos-r flex-0 mr-40tv">
      <img class="w-100p coin-img" src="../../assets/part7_2.png" alt="">
      <img class="w-100p" src="../../assets/part7_1.jpg" alt="">
    </div>
    <div>
      <div class="title-lg linear-color inline-block">Token Economics  Multi-chain Technology and Scaling</div>
      <!-- <div class="mt-8 subTitle">Web3bet 正在扩展以将体育投注体验带到所有兼容的网络  Tokenomics</div> -->
      <div class="flex mt-24">
        <div class="w-25p">
          <div class="gray-9d desc desc_mb-24">Token Name</div>
          <div class="desc">Web3bet Token</div>
        </div>
        <div class="w-25p">
          <div class="gray-9d desc desc_mb-24">Token ticker</div>
          <div class="desc">BET</div>
        </div>
        <div class="w-25p">
          <div class="gray-9d desc desc_mb-24">Token type</div>
          <div class="desc">ERC-20</div>
        </div>
        <div class="w-25p">
          <div class="gray-9d desc desc_mb-24">Token supply</div>
          <div class="desc">1,000,000,000</div>
        </div>
      </div>

      <div class="flex mt-60tv">
        <div class="w-50p flex">
          <img class="icon_w" src="../../assets/part7-1.png" alt="">
          <div class="ml-50tv">
            <div class="desc_title">Governance</div>
            <div class="desc">Hold BET tokens to gain voting rights on the protocol</div>
          </div>
        </div>
        <div class="w-50p flex">
          <img class="icon_w" src="../../assets/part7-2.png" alt="">
          <div class="ml-50tv">
            <div class="desc_title">Staking Reward</div>
            <div class="desc">Earn 50% of the profit of the capital pool since staking BET tokens</div>
          </div>
        </div>
      </div>

      <div class="flex mt-48">
        <LinearBox>
          <div class="primary font-size-14 info_btn px-48 py-8">More information
            <img style="margin-left: 4px" src="../../assets/arrow.png" alt="">
          </div>
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

<style lang="less" scoped>
.coin-img {
  position: absolute;
  top: 2vw;
  left: 42%;
  width: 5.2vw;
  animation: slide 5000ms ease-in-out infinite;
}
@keyframes slide {
  0% {
    transform: translateY(0) scale(1);
  }
  50% {
    transform: translateY(-20px) scale(1.1);
  }
  100% {
    transform: translateY(0) scale(1);
  }
}
.info_btn {
  user-select: none;
  -moz-user-select: none;
  -webkit-user-select: none;
  -o-user-select: none;
  &:active {
    color: #fff;
  }
}
.desc_title {
  font-size: 15px;
  font-weight: 600;
  margin-bottom: 8px;
  cursor: default;
  @media (min-width: 900px) and (max-width: 1440px) {
    font-size: 16px;
    margin-bottom: 10px;
  }
  @media (min-width: 1441px) and (max-width: 1919px) {
    font-size: 17px;
    margin-bottom: 11px;
  }
  @media (min-width: 1920px) {
    font-size: 18px;
    margin-bottom: 13px;
  }
}
.desc_mb-24 {
  margin-bottom: 1.25vw;
  cursor: default;
  // @media (min-width: 900px) and (max-width: 1440px) {
  //   margin-bottom: 20px;
  // }
  // @media (min-width: 1441px) and (max-width: 1919px) {
  //   margin-bottom: 20px;
  // }
  // @media (min-width: 1920px) {
  //   margin-bottom: 24px;
  // }
}
.mr-40tv {
  margin-right: 2vw;
}
.ml-50tv {
  margin-left: 2.6vw
}
.icon_w {
  width: 40px;
  height: auto;
  @media (min-width: 900px) and (max-width: 1440px) {
    margin-bottom: 48px;
  }
  @media (min-width: 1441px) and (max-width: 1919px) {
    margin-bottom: 50px;
  }
  @media (min-width: 1920px) {
    margin-bottom: 54px;
  }
}
.mt-60tv {
  margin-top: 3vw;
}
</style>