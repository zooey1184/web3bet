<template>
  <div style="padding-top: 10vw; padding-bottom: 25vh" class="flex color-white justify-between">
    <img src="../../assets/part1-bg.png" class="bg_img" alt="">
    <div style="z-index: 9">
      <div class="title-md">The first Betweb3.0 sports betting platform to achieve decentralized </div>
      <div class="flex items-center title-md">
        <div class="mr-8 title-md"></div>
        <div class="title-md linear-color">sports betting on the blockchain</div>
      </div>

      <div style="margin-top: 4vw">
        <div class="linear-bg inline-block launch_btn">Launch APP</div>
      </div>
      <div style="margin-top: 0.5vw">
        <div class="color-blue inline-block launch_btn">No sign-up required</div>
      </div>
      <div class="flex mt-24 items-center">
        <div class="gray desc">Audited by</div>
        <div class="mx-16">
          <img src="../../assets/logo.png" class="logo" alt="">
        </div>
        <div class="link desc">and more</div>
      </div>
    </div>
    <img class='w-100p' style="width: 24vw; height: auto;" src="../../assets/part1-gif.gif" />
  </div>
</template>

<style lang="less" scoped>
.bg_img {
  position: absolute;
  left: 7vw;
  top: 1.8vw
}
.launch_btn {
  padding: 8px 0;
  border-radius: 2px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 160px;
  font-size: 14px;
  @media (min-width: 900px) and (max-width: 1440px) {
    padding: 10px 0;
    width: 200px;
    font-size: 15px;
  }
  @media (min-width: 1441px) and (max-width: 1919px) {
    padding: 14px 0;
    width: 240px;
    font-size: 16px;
  }
  @media (min-width: 1920px) {
    padding: 16px 0;
    font-size: 17px;
    width: 280px;
  }
}
.desc {
  font-size: 13px;
  @media (min-width: 900px) and (max-width: 1440px) {
    font-size: 14px;
  }
  @media (min-width: 1441px) and (max-width: 1919px) {
    font-size: 15px;
  }
  @media (min-width: 1920px) {
    font-size: 16px;
  }
}
.logo {
  height: 26px;
  width: auto;
  padding-top: 2px;
  @media (min-width: 900px) and (max-width: 1440px) {
    height: 28px;
  }
  @media (min-width: 1441px) and (max-width: 1919px) {
    height: 30px;
  }
  @media (min-width: 1920px) {
    height: 33px;
  }
}
</style>