<template>
  <div class="flex items-center justify-between">
    <div class="flex items-center">
      <img src="../../assets/footer-logo.png" alt="">
      <div class="right">
        ©2021-嵌套-保留所有权利
      </div>
    </div>
    <div class="flex items-center">
      <img src="../../assets/footer.png" alt="">
      <div class="text">免责申明</div>
    </div>
  </div>
  <div style="margin-top: 26px" class="text-align-center gray-9 font-size-12">
    过往表现并不预示未来业绩。对区块链资产的任何投资都涉及损失部分或全部投资的风险。您交易所的区块链资产的价值受市场和其他投资风险的影响。
  </div>
</template>

<style lang="less" scoped>
.right {
  margin-left: 30px;
  @media (min-width: 900px) and (max-width: 1440px) {
    margin-left: 44px;
  }
  @media (min-width: 1441px) and (max-width: 1919px) {
    margin-left: 66px;
  }
  @media (min-width: 1920px) {
    margin-left: 99px;
  }
}
.text {
  margin-left: 30px;
  @media (min-width: 900px) and (max-width: 1440px) {
    margin-left: 50px;
  }
  @media (min-width: 1441px) and (max-width: 1919px) {
    margin-left: 99px;
  }
  @media (min-width: 1920px) {
    margin-left: 121px;
  }
}
</style>