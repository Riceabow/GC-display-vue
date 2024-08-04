<template>
    <div class ="pages" id="page3">
      <div class="bkdiv" id="bkdiv3" style="display: flex;flex-direction: column;">
      <div class="p3r" id="p3r1">
        <div class="p3head"></div>
      </div>
      <div class="p3r" id="p3r2">
        <div class="p3r2L" >
          <div class="p3r2 p3r2c1 p3fade" id="p3r2o1" ></div>
          <div class="p3r2 p3r2c1 p3fade" id="p3r2o2" ></div>
          <div class="Ltxt p3fade " id="Ltxt1" ></div>
          <div class="Ltxt p3fade" id="Ltxt2" ></div>
        </div>
        
        <div class="p3r2m p3fade">
          <ColorPicker v-model="colorElected" size="medium" modebar="none" style="position: absolute;;left: 0;top: 0;" />
          <!-- <p style="position: absolute;left: 50px;top: 0;color: #f19600;">拾色器</p> -->
          <div class="mstuffs" id="p3m1" ref="outer"></div>
          <div class="mstuffs" id="p3m2" ref="inner"></div>
          <div class="mstuffs" id="p3m3"></div>
          <div class="mstuffs" id="p3m4" ref="blurColor" :style="bkcolor"></div>
        </div>

        <div class="p3r2R" ref="p3r2R">
          <div class="p3r2 p3fade" id="p3r2o3" ></div>
          <div class="p3r2 p3fade" id="p3r2o4" ></div>
          <div class="p3r2 p3fade" id="p3r2o5" ></div>
          <div class="Rtxt p3fade" id="Rtxt1" ></div>
          <div class="Rtxt p3fade" id="Rtxt2"></div>
        </div>

      </div>
      <div class="p3r" id="p3r3" ref="p3r3">
        <div id="p3r3r1">
          <div id="p3r3head"></div>
        </div>
        <div id="p3r3r2">
          <div class="p3r3r2c" id="p3r3r2c1">
            <img class="rotate-img" src="/images/P3/18.png" alt="" width="100%">
          </div>
          <div class="p3r3r2c" id="p3r3r2c2"></div>
          <div class="p3r3r2c rotate-div" id="p3r3r2c3">
            <img class="rotate-img" src="/images/P3/18.png" alt="" width="100%">
          </div>
          <div class="p3r3r2c" id="p3r3r2c4"></div>
          <div class="p3r3r2c rotate-div" id="p3r3r2c5">
            <img class="rotate-img" src="/images/P3/18.png" alt="" width="100%">
          </div>
          <div class="p3r3r2c" id="p3r3r2c6"></div>
        </div>
      </div>
      </div>
    </div>
</template>
<script>
import gsap from 'gsap';  
import { ScrollTrigger } from "gsap/ScrollTrigger";  
import ColorPicker from '@mcistudio/vue-colorpicker'
import '@mcistudio/vue-colorpicker/dist/style.css'

export default{
  name:'Page3',
  components: {  
    ColorPicker  
  },
  data() {  
    // 使用 data 函数返回一个对象，其中包含响应式数据  
    return {  
      colorElected: {  
        color: { r: 246, g: 185, b: 79, a: 1 } // 初始颜色值  
      }  
    };  
  },
  computed:{
    bkcolor(){  
      const { r, g, b, a } = this.colorElected.color;  
      // 注意：这里我们简化了渐变，只设置了一个颜色和透明度变化点  
      // 你可以根据需要调整渐变的其他部分  
      const gradient = `radial-gradient(circle, rgba(${r},${g},${b},${a}) 40%, rgba(${r},${g},${b},0) 100%)`;  
      const shadow = `0 0 40px 30px rgba(${r},${g},${b},0.5)`;  
      // 返回一个包含所有样式的对象  
      return {  
        // height: '50%',  
        // zIndex: 1,  
        // borderRadius: '50%',  
        background: gradient, // 注意：这里我们使用 backgroundColor 来覆盖 background 属性中的渐变部分  
        // 如果你还需要保留 background 属性中的其他值（如背景图片），则需要更复杂的处理  
        boxShadow: shadow,  
      };  
  }
},
  mounted() {  
    gsap.registerPlugin(ScrollTrigger);  
      const p3Ani = gsap.timeline({ 
        scrollTrigger: {  
          trigger: "#page3",  
          start: "top top",  
          // markers:true,
          end: "top top", 
          // scrub: true, // 允许用户通过滚动回溯动画  
        }  
      }) 
     this.middleAni(p3Ani);

     this.bottomAni(p3Ani);
    } ,

  methods: {  
    bottomAni(tl){
      const bigDiv = this.$refs.p3r3;  
      gsap.set(bigDiv, { yPercent: 100 });  
      const rotateDivs = bigDiv.querySelectorAll('.rotate-img');  
  
      // 先将大div隐藏到屏幕下方  
  
      // 滚动到#page3时，大div从下往上弹出  
      tl.fromTo(bigDiv, { yPercent: 100 }, {  
        yPercent: 0,  
        duration: 2, // 弹出动画的持续时间  
        ease: "power1.out"
      },'<');  
  
      // 同时，三个小div开始无限旋转  
      rotateDivs.forEach(div => {  
        tl.to(div, {  
          duration: 15, // 动画持续时间，秒  
          rotation: "360", // 旋转角度  
          ease: "none", // 缓动函数  
          repeat: -1, // 无限重复  
        },"<");  
      });  
    },
    shadeAccumulation(el,points){

              const angle = gsap.getProperty(el, "rotation"); // 获取当前的旋转角度
              const radians = angle * (Math.PI / 180); // 将角度转换为弧度
              
              // 计算 clip-path 的当前端点，以形成旋转的细长三角形遮罩
              const radius = 71; // 计算外切圆半径，√2/2 * 100 ≈ 71%
              const x = 50 + radius * Math.cos(radians); // 计算当前点的 x 坐标
              const y = 50 + radius * Math.sin(radians); // 计算当前点的 y 坐标

              // 将当前计算的点添加到 points 数组中，累积显示的区域
              points.push({x, y});

              // 动态更新 clip-path，形成累积遮罩区域
              const clipPathValue = `polygon(${points.map(p => `${p.x}% ${p.y}%`).join(', ')})`;
              el.style.clipPath = clipPathValue;
     },
    middleAni(tl){
      const fades =document.querySelectorAll(".p3fade")
      const outer = this.$refs.outer
      const inner = this.$refs.inner
      fades.forEach(fade =>{
        gsap.set(fade,
          {
            opacity: 0, 
          }
        )
      })
      const points = [
                  {x: 50, y: 50} // 初始点，在中心
              ];
      tl.to(outer, {
          duration: 3, // 动画持续时间 5 秒
          ease: "none", // 线性缓动，保证匀速旋转
          onUpdate:function(){
            const angle = gsap.getProperty(outer, "rotation"); // 获取当前的旋转角度
              const radians = angle * (Math.PI / 180); // 将角度转换为弧度
              
              // 计算 clip-path 的当前端点，以形成旋转的细长三角形遮罩
              const radius = 71; // 计算外切圆半径，√2/2 * 100 ≈ 71%
              const x = 50 + radius * Math.cos(radians); // 计算当前点的 x 坐标
              const y = 50 + radius * Math.sin(radians); // 计算当前点的 y 坐标

              // 将当前计算的点添加到 points 数组中，累积显示的区域
              points.push({x, y});

              // 动态更新 clip-path，形成累积遮罩区域
              const clipPathValue = `polygon(${points.map(p => `${p.x}% ${p.y}%`).join(', ')})`;
              outer.style.clipPath = clipPathValue;
          },
          rotation: -360, // 逆时针旋转 360 度
          transformOrigin: "50% 50%", // 以 div 的中心为旋转中心
          onComplete:function(){
            outer.style.clipPath = 'none';
          }
      });
      tl.to(inner, {
          duration: 3, // 动画持续时间 5 秒
          ease: "none", // 线性缓动，保证匀速旋转
          onUpdate:function(){
            const angle = gsap.getProperty(inner, "rotation"); // 获取当前的旋转角度
              const radians = angle * (Math.PI / 180); // 将角度转换为弧度
              
              // 计算 clip-path 的当前端点，以形成旋转的细长三角形遮罩
              const radius = 71; // 计算外切圆半径，√2/2 * 100 ≈ 71%
              const x = 50 + radius * Math.cos(radians); // 计算当前点的 x 坐标
              const y = 50 + radius * Math.sin(radians); // 计算当前点的 y 坐标

              // 将当前计算的点添加到 points 数组中，累积显示的区域
              points.push({x, y});

              // 动态更新 clip-path，形成累积遮罩区域
              const clipPathValue = `polygon(${points.map(p => `${p.x}% ${p.y}%`).join(', ')})`;
              inner.style.clipPath = clipPathValue;
          },
          rotation: -360, // 逆时针旋转 360 度
          transformOrigin: "50% 50%", // 以 div 的中心为旋转中心
          onComplete:function(){
            inner.style.clipPath = 'none';
          }
      },'<');
      fades.forEach(fade =>{
        tl.to(fade,
          {
            opacity: 1, // 目标透明度为1，即完全可见  
            duration: 5, // 动画持续时间为1秒  
            ease: 'power1.out' // 使用缓动函数，让动画看起来更自然 
          },"<"
        )
      })
     },
     
    }

}

</script>

<style>
  @import '../assets/style/P3.css';
  @import '../assets/style/style.css';

</style>