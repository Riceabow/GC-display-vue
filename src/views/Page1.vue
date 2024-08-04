<template>
    <div class="pages" id="page1">
      <div class="bkdiv" id="bkdiv1" style="display: flex;justify-content: center;z-index: -100;">
        <div id="bkdiv12" style="z-index: 2;"></div>
        <div id="pingzi" style="z-index: 1;">
          <img src="/images/pingzi.png" alt="" height="200px" />
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import { gsap } from "gsap";  
  import { ScrollTrigger } from "gsap/ScrollTrigger";  
  gsap.registerPlugin(ScrollTrigger);
  export default {
    name: 'Page1',

    mounted(){
      ScrollTrigger.create({
        trigger:"#page1",
        start:"top top",
        // markers:true,
        end:"+=400 0",
        scrub:true,
        pin:true,
        animation:gsap.to('#pingzi',{scale:4})
    }
    )
    }
  }
  </script>
  
  <style scoped>
  @import '../assets/style/P1.css';
  @import '../assets/style/style.css';

  </style>
  