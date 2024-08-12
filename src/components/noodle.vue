<template>
    <div class="process-section">

      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 843.02 742.82">
                <g id="layer1" data-name="layer1">
                    <path class="cls-1" ref="noodlePath" d="M50,276.66l544.84-219a106.81,106.81,0,0,1,62.65-5.23l1.48.32a105.82,105.82,0,0,1,57.94,34.4c34.94,40.58,32.68,105.25-3.32,144.9-12.11,13.34-29.49,27-42.37,32.24l-527,213.61c-13.86,5.62-34.16,20.25-48.12,40.24-30.34,43.46-31.64,100,3.78,139.39a106,106,0,0,0,50,31.13h0a106.67,106.67,0,0,0,69.11-3.55L793,455"/>
                    <!-- <path class="cls-1" ref="noodlePath" d="M787.22,465.06,201.37,701.38A109.24,109.24,0,0,1,59.2,640.94L58,637.86A109.24,109.24,0,0,1,118.4,495.69l575.27-232a109.24,109.24,0,0,0,60.44-142.16l-1.25-3.08A109.22,109.22,0,0,0,610.7,58L61.78,279.38"/> -->
                </g>

        </svg>


    </div>
  </template>
  
  <script>
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";
  
  gsap.registerPlugin(ScrollTrigger);
  
  export default {
    data() {
            return {
                game: '启动!!!'
            }
        },

    mounted() {
      const noodlePath = this.$refs.noodlePath;
      gsap.fromTo(noodlePath, { strokeDasharray: "0 1000" }, { strokeDasharray: "1000 0", duration: 10, ease: "power1.inOut" });
      // Add more animations to other lines
    }
  };
  </script>
  
  <style scoped>
  .process-section{
    width: 100%;
  }
  .cls-1{
    fill:none;
    stroke:#f3d7a1;
    stroke-linecap:round;
    stroke-miterlimit:10;
    stroke-width:100px;}
  </style>