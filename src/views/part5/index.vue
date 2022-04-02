<template>
  <div class="gutter_col flex justify-between">
    <div style="width: 40%; padding-top: 11vh">
      <Steps :options="options" />
    </div>

    <div style='width: 50%'>
      <div class="linear-color title-lg inline-block">轻松使用产品</div>
      <div class="mt-24 desc">Web3bet 在利用区块链技术的同时为了易于使用还原且优化了传统的体育投注平台的交互体验</div>
      <div class="flex justify-end" style="margin-top: 10vh">
        <div style="height: 16.5vw; width: 24vw" class="bg-gray-30">
      </div>
      </div>
    </div>
  </div>
</template>

<script>
import { defineComponent, ref } from 'vue'
import Steps from '../../components/steps'

export default defineComponent({
  components: {
    Steps
  },
  props: {},
  setup(props) {
    return {
      options: [
        {
          label: '连接钱包'
        },
        {
          label: '选择钱包并连接选择赛事'
        },
        {
          label: '选择足球，篮球，电子竞技的赛事进行投注'
        },
        {
          label: '选择盘口'
        },
        {
          label: '等待区块确认'
        },
        {
          label: '资金池将'
        }
      ]
    }
  }
})
</script>