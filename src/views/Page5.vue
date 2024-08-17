<template>
   <div class ="pages" id="page5"   >
    <div class="bkdiv" id="bkdiv5" style="display: flex;" @click="toggleElse($event)" >
        <div class="p5head"></div>
        <div class="process-section" id="noodle">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 843.02 742.82">
                    <g id="layer1" data-name="layer1">
                        <path class="cls-1" ref="noodlePath" d="M50,276.66l544.84-219a106.81,106.81,0,0,1,62.65-5.23l1.48.32a105.82,105.82,0,0,1,57.94,34.4c34.94,40.58,32.68,105.25-3.32,144.9-12.11,13.34-29.49,27-42.37,32.24l-527,213.61c-13.86,5.62-34.16,20.25-48.12,40.24-30.34,43.46-31.64,100,3.78,139.39a106,106,0,0,0,50,31.13h0a106.67,106.67,0,0,0,69.11-3.55L793,455"/>
                    </g>
            </svg>
        </div>
        <!-- <noodle id="noodle"/> -->
        <div class="" id="p5c1" ref="p5c1">
            <div id="p5c1head"></div>
            <div class="" id="tools"></div>
        </div>
        <div class="" id="p5c2">
            <div id="p5c2head" ></div>
        </div>
    </div>
    <div  
      v-for="n in 10"  
      :key="n"  
      class="illustrations"  
      :id="'illu' + n"
      @click="toggleIllustration($event)"    
    ></div>  
   </div>
</template>
<script>
import gsap from 'gsap';  
import { ScrollTrigger } from "gsap/ScrollTrigger";  
import noodle from '../components/noodle.vue';

export default{
    name:'Page5',
    components: {
    noodle
  },
    
    mounted() {  
    const noodlePath = this.$refs.noodlePath;
    const illus = document.querySelectorAll(".illustrations")
    illus.forEach(illu=>{
        gsap.set(illu,{ opacity:0,})
      })
    gsap.registerPlugin(ScrollTrigger);  
      const p5ani = gsap.timeline({ 
        scrollTrigger: {  
          trigger: "#page5",  
          start: "top top",  
          // markers:true,
          end: "+=300", 
          pin: true,
        }  
      }) 
      const leftObj = this.$refs.p5c1;  
      gsap.set(leftObj, { xPercent: -100 });  
      p5ani.to(leftObj,{ xPercent: 0, 
        duration: 2, // 弹出动画的持续时间  
        ease: "power1.out"})

      illus.forEach(illu=>{
        p5ani.to(illu,{ opacity:1,
        duration: 0.8, // 弹出动画的持续时间  
        ease: "power1.out"},"-=0.4")
      })
      p5ani.fromTo(noodlePath, 
      { strokeDasharray: "0 1000" }, 
      { strokeDasharray: "1000 0", duration: 5, ease: "power1.inOut" },
      "-=4");
    },
    methods:{
      toggleIllustration(event) {  
      const target = event.target;  
      const illustrations = document.querySelectorAll('.illustrations');  
      illustrations.forEach(illu =>{
        if (illu != target) {
          gsap.to(illu, {  
        duration: 0.3,
        opacity:0,  
        display: "none",  
        stagger: 0.05,  
        ease: "power1.out",  
        exceptSelf: true // GSAP 3.x 特性，确保当前hover的元素不被影响  
      });  
        }  
      })
      // 初始化其他元素的透明度动画  
     
  
      // // 放大并移动到中心  
      // const container = document.getElementById('page5');  
      // const centerX = container.offsetWidth / 2;  
      // const centerY = container.offsetHeight / 2;  
      // const currentX = target.offsetLeft + target.offsetWidth / 2;  
      // const currentY = target.offsetTop + target.offsetHeight / 2;  
  
      gsap.to(target, {  
        duration: 0.3, 
        opacity: 1,  
        scale: 2,  
        top: "30vh",
        left: "50vw",
        ease: "power1.out"  
      });  
    },  
    toggleElse() {  
      const illustrations = document.querySelectorAll('.illustrations');  
  
      // 恢复所有元素的原始状态  
      gsap.to(illustrations, {  
        duration: 0.3,  
        display:"block",
        opacity: 1,  
        scale: 1, 
        top: "",
        left: "", 
        x: 0,  
        y: 0,  
        ease: "power1.inOut",  
        stagger: 0.05  
      });  
    }  
    }

    }
</script>

<style>
  @import '../assets/style/P5.css';
  @import '../assets/style/style.css';
  .process-section{
    height: 100%;
  }
  .cls-1{
    fill:none;
    stroke:#f3d7a1;
    stroke-linecap:round;
    stroke-miterlimit:10;
    stroke-width:100px;}
</style>