<template>
    <div class ="pages" id="page4">
      <div class="bkdiv" id="bkdiv4" style="display: flex;flex-direction: column;">
        <div class="arch-bridge" ref="AB" >  
            <div id="P4head"></div>
            <div class="P4headTxt" id="headTxt1" ref="leftHtxt"></div>
            <div class="P4headTxt" id="headTxt2" ref="rightHtxt"></div>
            <div class="arch-shade" ref="AS"></div>
        </div>  
        <div id="dial" ref="dial">
            <div class="Spreadinfos" id="p4info1"></div>
            <div class="Spreadinfos" id="p4info2"></div>
            <div class="Spreadinfos" id="p4info3"></div>
            <div class="Spreadinfos" id="p4info4"></div>
            <div class="Spreadinfos" id="p4info5"></div>
            <div class="Spreadinfos" id="p4info6"></div>
            <div class="Spreadinfos" id="p4info7"></div>
            <div class="Spreadinfos" id="p4info8"></div>
            <div class="Spreadinfos" id="p4info9"></div>
            <div class="Spreadinfos" id="p4info10"></div>
            <div class="Spreadinfos" id="p4info11"></div>
            <div class="Spreadinfos" id="p4info12"></div>
            <div class="Spreadinfos" id="p4info13"></div>
            <div class="Spreadinfos" id="p4info14"></div>
            <div class="Spreadinfos" id="p4info15"></div>
            <div class="Spreadinfos" id="p4info16"></div>
            <div class="Spreadinfos" id="p4info17"></div>
            <div class="Spreadinfos" id="p4info18"></div>
            <div class="Spreadinfos" id="p4info19"></div>
            <div class="Spreadinfos" id="p4info20"></div>
            <div class="Spreadinfos" id="p4info21"></div>
            <div class="Spreadinfos" id="p4info22"></div>
            <div class="Spreadinfos" id="p4info23"></div>
            <div class="Spreadinfos" id="p4info24"></div>
        </div>

        <div id="pingziInp4" ref="p4PZ">
        </div>

     </div>
   </div>
</template>
<script>
import gsap from 'gsap';  
import { ScrollTrigger } from "gsap/ScrollTrigger";  
export default{
    Name:'Page4',
    mounted() { 
        const pz = this.$refs.p4PZ
        const dial = this.$refs.dial
        gsap.set(dial,{
        scale:0,})
        gsap.set(pz,{
            scale:0,})
        gsap.registerPlugin(ScrollTrigger);  
        const p4ani = gsap.timeline({ 
            scrollTrigger: {  
            trigger: "#page4",  
            start: "top top",  
            // markers:true,
            end: "+=300", 
            pin: true,
            }  
        }) 
        this.ASwoggle(p4ani)
        this.dialScale(p4ani)
    },
    methods:{
        ASwoggle(tl){
            const AB = this.$refs.AB
            const AS = this.$refs.AS;
            const LHtxt = this.$refs.leftHtxt
            const RHtxt = this.$refs.rightHtxt
            tl.set(AS,{ height:"0",})
            tl.set(LHtxt,{ x:"50%", opacity:0})
            tl.set(RHtxt,{ x:"-50%", opacity:0})

            tl.set(AB,{
                y:"-100%"
            })
            tl.to(AB,{
                y:0,
                duration:2
            })
            tl.to(AS,
                {
                height:"300%",
                backgroundColor:"#fdf6ec",
                top:"30%",
                duration: 2,
                },"-=0.5"
            )
            tl.to(LHtxt,{
                x:0, opacity:1,duration:1.2
            })
            tl.to(RHtxt,{
                x:0, opacity:1,duration:1.2
            },"<")
        },
        dialScale(tl){
            const pz = this.$refs.p4PZ
            const dial = this.$refs.dial
            tl.to(dial,{
                scale:1.2,duration:1,
            })
            tl.to(pz,{
                scale:1
            },"<")
            tl.to(dial,{
                scale:1
            })
            
        }


    }


}

</script>

<style>
  @import '../assets/style/P4.css';
  @import '../assets/style/style.css';

</style>