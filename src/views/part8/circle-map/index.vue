<template>
  <div class="pos-r" style="height: 19.375vw; width: 40.75vw">
    <div class="pos-a top-0 left-0">
      <Circle rotate='40' size='8.54vw' desc='2022Q2' @click='state.active = 0' :solid="state.active === 0">
        <div class="color-white p-16 flex flex-col items-center">
          <img class="w-85p" src="../../../assets/2022q2.gif" alt="">
          <!-- <div class="text-align-center mt-8 desc-item">
            2022Q2
          </div> -->
        </div>
      </Circle>
    </div>
    <div class="q3_2022">
      <Circle rotate='315' size='8.17vw' desc='2022Q3' @click='state.active = 1' :solid="state.active === 1">
        <div class="color-white p-8 flex justify-center items-center">
          <img class="w-90p" style="margin-top: 4px" src="../../../assets/2022q3.gif" alt="">
          <!-- <div class="text-align-center mt-8 desc-item">
            2022Q3
          </div> -->
        </div>
      </Circle>
    </div>
    <div class="q4_2022">
      <Circle :showLine="false" size='7.8vw' desc='2022Q4' @click='state.active = 2' :solid="state.active === 2">
        <div class="color-white p-16 flex flex-col items-center">
          <img class="w-85p" src="../../../assets/2022q4.gif" alt="">
          <!-- <div class="text-align-center mt-8 desc-item">
            2022Q4
          </div> -->
        </div>
      </Circle>
    </div>
    <div class="q1_2023">
      <Circle rotate='225' size='10.67vw'  desc='2023Q1' @click='state.active = 3' :solid="state.active === 3">
        <div class="color-white p-16 flex flex-col items-center">
          <img class="w-80p mt-8" src="../../../assets/2023q1.gif" alt="">
          <!-- <div class="text-align-center mt-8 desc-item">
            2023Q1
          </div> -->
        </div>
      </Circle>
    </div>
    <div class="q2_2023">
      <Circle :rotate="135" size='7.8vw'  desc='2023Q2'  @click='state.active = 4' :solid="state.active === 4">
        <div class="color-white p-16 flex flex-col items-center">
          <img class="w-80p mt-8" src="../../../assets/2023q2.gif" alt="">
          <!-- <div class="text-align-center mt-8 desc-item">
            2023Q2
          </div> -->
        </div>
      </Circle>
    </div>
  </div>
</template>

<script>
import { defineComponent, reactive, ref, watch } from 'vue'
import Circle from '../circle'

export default defineComponent({
  components: {
    Circle
  },
  props: {
    active: {
      type: Number,
      default: 0
    }
  },
  emits: ['update:active', 'change'],
  setup(props, {emit}) {
    const state = reactive({
      active: props.active
    })

    watch(() => props.active, (n) => {
      state.active = n
    })

    watch(() => state.active, (n) => {
      emit('update:active', n)
      emit('change',n )
    })

    return {
      state
    }
  }
})
</script>

<style lang="less" scoped>
.q3_2022 {
  position: absolute;
  left: 8.54vw;
  top: 6.4vw;
}
.q4_2022 {
  position: absolute;
  left: 16.04vw;
  top: -1.51vw;
}
.q1_2023 {
  position: absolute;
  left: 23.9vw;
  top: 6.4vw;
}
.q2_2023 {
  position: absolute;
  left: 33.4vw;
  top: 0;
}
.desc-item {
  font-size: 12px;
  margin-top: 4px;
  @media (min-width: 900px) and (max-width: 1440px) {
    font-size: 13px;
    margin-top: 5px;
  }
  @media (min-width: 1441px) and (max-width: 1919px) {
    font-size: 14px;
    margin-top: 6px;
  }
  @media (min-width: 1920px) {
    font-size: 14px;
    margin-top: 8px;
  }
}
</style>