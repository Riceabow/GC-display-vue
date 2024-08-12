<template>
   <div class ="pages" id="page6">
    <div class="bkdiv" id="bkdiv6" style="display: flex;flex-direction: column;">
        <div class="p6r" id="p6r1">
            <div class="p6head"></div>
        </div>
        <div class="p6r" id="p6r2">
            <div class="p6r2c" id="p6r2c1">
                <div class="p6r2c1r" id="p6r2c1r1">
                    <div class="p6r2c2r1c fades" id="p6r2c1r1c1">
                        <div id="p6r2c1r1c1head"></div>
                        <div id="p6r2c1r1c1o"></div>
                    </div>
                    <div class="p6r2c2r1c fades" id="p6r2c1r1c2">
                        <div id="p6r2c1r1c2head"></div>
                        <div id="p6r2c1r1c2o"></div>
                    </div>
                </div>
                <div class="p6r2c1r " id="p6r2c1r2">

                    <div class="p62c1r2o fades" id="p6r2c1r2o1"></div>
                    <div class="p62c1r2o fades" id="p6r2c1r2o2"></div>
                    <div class="p62c1r2o fades" id="p6r2c1r2o3"></div>
                    <div class="fades" id="p6r2c1r2head"></div>
                    <div class="fades" id="p6r2c1r2o"></div>
                </div>
            </div>
            <div class="p6r2c" id="p6r2c2">
                <div class="p6r2c2r fades" id="p6r2c2r1">
                    <div id="p6r2c2r1head"></div>
                    <div id="p6r2c2r1o"></div>
                </div>
                <div class="p6r2c2r fades" id="p6r2c2r2">
                    <div id="p6r2c2r2head"></div>
                    <div class="p6r2c2r2r">
                            <sankey  id="p6r2c2r2o"/>
                            <div id="sankeyTxt">
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
   </div>
</template>

<script>
import gsap from 'gsap';  
import { ScrollTrigger } from "gsap/ScrollTrigger";  
import sankey from '../components/sankey.vue';
export default{
    name:'Page6',
    components:{
        sankey,
    },
    mounted(){

        const fades = document.querySelectorAll(".fades")
        fades.forEach(fade=>{
        gsap.set(fade,{ opacity:0,})
      })
    gsap.registerPlugin(ScrollTrigger);  
      const p6ani = gsap.timeline({ 
        scrollTrigger: {  
          trigger: "#page6",  
          start: "top top",  
        //   markers:true,
          end: "top top", 
          // scrub: true, // 允许用户通过滚动回溯动画  
        }  
      }) 
      fades.forEach(fade=>{
        p6ani.to(fade,{ opacity:1,
        duration: 0.8, // 弹出动画的持续时间  
        ease: "power1.out"},"-=0.3")

      })
    }

    }

</script>

<style>
@import '../assets/style/P6.css';
@import '../assets/style/style.css';

</style>