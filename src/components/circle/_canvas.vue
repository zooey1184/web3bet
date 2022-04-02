<template>
  <canvas :width="canvasRadius" :height="canvasRadius" @mouseenter="handleMouseEnter" @mouseleave="handleMouseLeave" ref="canvas"></canvas>
</template>

<script>
import { computed, defineComponent, onMounted, ref } from "vue";

export default defineComponent({
  components: {},
  props: {
    radius: {
      type: [String, Number],
      default: 510
    }
  },
  setup(props) {
    const canvas = ref();
    const RADIUS = props.radius
    const OFFSET = 6
    const canvasRadius = computed(() => Number.parseInt(RADIUS) + OFFSET)

    const isStop = ref(false)

    const handleMouseEnter = (e) => {
      isStop.value = true
    }
    const handleMouseLeave = (e) => {
      isStop.value = false
    }

    onMounted(() => {
      const ctx = canvas.value.getContext("2d");
      function drawTrack() {
        for (var i = 0; i < 4; i++) {
          ctx.beginPath();
          
          ctx.arc((RADIUS+4)/2, (RADIUS+4)/2, (i + 1) * 50, 0, 2 * Math.PI, false);
          // const gt = ctx.createRadialGradient(RADIUS, RADIUS, 30, RADIUS+50, RADIUS+50, 130)
          const gt = ctx.createLinearGradient(0, 0, RADIUS * 2, RADIUS * 2)
          gt.addColorStop(0, '#f8d68e');
          gt.addColorStop(0.3, '#f2a0be')
          gt.addColorStop(0.5, '#2fc2c7')
          gt.addColorStop(0.8, '#376dfa');
          gt.addColorStop(1, '#376dfa');
          // ctx.strokeStyle = "#fff";
          ctx.strokeStyle = gt
          ctx.stroke();
          ctx.closePath();
        }
      }
      drawTrack();

      class Star {
        constructor(x, y, radius, cycle, sColor, eColor) {
          this.x = x;
          this.y = y;
          this.radius = radius;
          this.cycle = cycle;
          this.sColor = sColor;
          this.eColor = eColor;

          this.color = null;
          this.time = 0;
          this.dampx = 2 // 阻尼系数
          const img = new Image()
          img.src = 'https://tva1.sinaimg.cn/large/e6c9d24ely1h0m4su187ej21s20u0796.jpg'
          this.img = img
          this.step = 0
        }
        draw(ctx, isStop) {
          ctx.beginPath();
          ctx.save();
          ctx.translate(RADIUS/2, RADIUS/2);
          // ctx.rotate((((this.time * 360) / this.cycle) * Math.PI) / 180);
          // const step = (((this.time * 360) / this.cycle) * Math.PI) / 180
          this.step += Math.PI/(600 + this.cycle)
          this.x = this.radius * Math.cos(this.step)
          this.y = this.radius * Math.sin(this.step);
          ctx.arc(this.x, this.y, 20, 0, 2 * Math.PI, false);
          
          this.color = ctx.createRadialGradient(
            this.x,
            this.y,
            0,
            this.x,
            this.y,
            this.radius
          );
          this.color.addColorStop(0, this.sColor);
          this.color.addColorStop(1, this.eColor);
          ctx.fillStyle = this.color;
          ctx.fill();
          ctx.clip()
          
          ctx.drawImage(this.img, this.x-this.radius, this.y-this.radius, 50, 50);
          ctx.restore();
          
          // img.onload = () => {
            
          // }
          ctx.closePath();
          if (!isStop) {
            this.time += 1;
            this.dampx = 2
          } else {
            this.dampx += 0.3
            this.time += (1/this.dampx);
          }
          
        }
      }

      //创建各个星球类，通过伪继承
      // function Earth(){
      // 	Star.call(this,0,-150,10,365,"#78b1eb","#050c12")
      // }
      // function Mars(){
      // 	Star.call(this,0,-200,10,687,"#cec999","#76422d")
      // }

      // function Jupiter(){
      // 	Star.call(this,0,-250,10,4333,"#c0a48e","#322222")
      // }
      // function Saturn(){
      // 	Star.call(this,0,-300,10,10766,"#f7f9e3","#1F1666")
      // }
      // function Uranus(){
      // 	Star.call(this,0,-350,10,30799,"#a7e1e8","#19243a")
      // }
      // function Neptune(){
      // 	Star.call(this,0,-400,10,60129,"#0661b2","#1e3b73")
      // }

      //根据各个星球类创建实例对象
      // var earth=new Earth()
      // var mars=new Mars()
      const sun = new Star(0, 0, 150, 10, "#f00", "#f00");
      const mercury = new Star(0, -150, 100, -80, "#A69888", "#5c3666");
      const venus = new Star(0, -100, 200, -300, "#C4BBAC", "#1F1666");

      
      

      // var jupiter=new Jupiter()
      // var saturn=new Saturn()
      // var uranus=new Uranus()
      // var neptune=new Neptune()

      function move(isStop) {
        ctx.clearRect(0, 0, 1000, 1000);
        drawTrack();

        sun.draw(ctx);
        mercury.draw(ctx, isStop);
        venus.draw(ctx, isStop);
      }
      function anim() {
        requestAnimationFrame(function () {
          if (!isStop.value) {
            move();
          } else {
            move(true);
          }
          
          anim();
        });
      }
      anim();
    });

    return {
      canvas,
      canvasRadius,
      handleMouseEnter,
      handleMouseLeave
    };
  },
});
</script>


<style lang="less" scoped>
.canvas {
  width: 50vw;
  height: 50vw;
}
</style>