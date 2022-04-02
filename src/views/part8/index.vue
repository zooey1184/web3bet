<template>
  <div class="mb-48">
    <div style="margin-bottom: 26px" class="inline-block linear-color title-lg">Road map</div>
    <div class="subTitle"  style="margin-bottom: 63px">We are also working on ex、panding the Web3bet ecosystem.Stay tuned…</div>

    <div style="width: 30%;">
      <Steps :options="options" />
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
