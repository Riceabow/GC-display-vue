<template>
    <div class="pages" id="page2">
      <div class="bkdiv" id="bkdiv2" style="display: flex;flex-direction: column;">
        <div class="flexBox" id="p2r1" style="position: relative;">
          <div class="p2box" id="p2head" style="margin-left: 100px;"></div>
        </div>
        <div id="p2r2" class="flexBox">
          <div class="p2box p2left" id="p2r2c1">
            <div id="p2r2c1r1"></div>
            <div id="p2r2c1r2"></div>
            <div id="p2r2c1r4"></div>
            <div id="p2r2c1r3">
              <div class="lineAniContainer">
                <div class="line-container" id="line1">
                  <div class="line"></div>
                  <div class="number">0</div>
                </div>
                <div class="line-container" id="line2">
                  <div class="line"></div>
                  <div class="number">0</div>
                </div>
                <div class="line-container" id="line3">
                  <div class="line"></div>
                  <div class="number">0</div>
                </div>
              </div>
            </div>
          </div>
          <div class="p2box" id="p2r2c2">
            <div id="p2r2c2r1"></div>
          </div>
        </div>
        <div class="flexBox" id="p2r3">
          <div class="p2box p2left" id="p2r3c1">
            <div id="p2r3c1r1"></div>
            <div id="p2r3c1r2"></div>
          </div>
          <div class="p2box" id="p2r3c2">
            <div id="p2r3c2r1"></div>
            <div id="p2r3c2r2">
              <div class="circle" id="circle1" style="top: 0; left: 0;"></div>
              <div class="p2txt hidden" id="p2t1" style="top: 50px; left: 2%; height:38%; width: 20%;position: relative;"></div>
              <div class="p2txt hidden" id="p2t2" style="top: 60px ;left: 2%; height:38%; width: 20%;position: relative;"></div>
              <div class="line" id="line1" style="top: 20px; left: 20px; height:10px; width: 0;"></div>
              <div class="line" id="line2" style="left: calc(25% - 5px); top: 25px; width: 10px; height: 0;"></div>
              <div class="circle hidden" id="circle2" style="bottom: 0; left: calc(25% - 25px); transform: scale(0);"></div>
              <div class="p2txt hidden" id="p2t3" style="bottom:50px ;left: 27%; height:80%; width: 20%;position: absolute;"></div>
              <div class="line" id="line3" style="left: calc(25% - 5px); bottom:20px ;height:10px; width: 0;"></div>
              <div class="line" id="line4" style="left: calc(50% - 5px); bottom: 20px; width: 10px; height: 0;"></div>
              <div class="circle hidden" id="circle3" style="top: 0; left: calc(50% - 25px); transform: scale(0);"></div>
              <div class="p2txt hidden" id="p2t4" style="top:50px ;left: 52%; height:70%; width: 21%;position: absolute;"></div>
              <div class="line" id="line5" style="left: calc(50% - 5px); top:20px; height:10px; width: 0;"></div>
              <div class="circle hidden" id="circle4" style="top: 0; left: calc(75% - 25px); transform: scale(0);"></div>
              <div class="p2txt hidden" id="p2t5" style="bottom:50px ;left: 77%; height:68%; width: 18%;position: absolute;"></div>
              <div class="line" id="line6" style="left: calc(75% - 5px); top: 20px; width: 10px; height: 0;"></div>
              <div class="line" id="line7" style="left: calc(75% - 5px); bottom:20px ;height:10px; width: 0;"></div>
              <div class="circle hidden" id="circle5" style="right: 0; bottom: 0;transform: scale(0);"></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import { gsap } from "gsap";  
  import { ScrollTrigger } from "gsap/ScrollTrigger";  
  gsap.registerPlugin(ScrollTrigger);
  export default {
    
    name: 'Page2',
    mounted() {
      const lines = [
        { id: "#line1",  number: "#line1 .number", targetNumber: 58 },
        { id: "#line2",  number: "#line2 .number", targetNumber: 295 },
        { id: "#line3",  number: "#line3 .number", targetNumber: 89 }
      ];
  
      gsap.registerPlugin(ScrollTrigger);
  
      const tlp2 = gsap.timeline({
        scrollTrigger: {
          trigger: "#page2",
          start: "top top",
          end: "+=800 0",
          scrub: true,
          pin: true
        }
      });
  
      lines.forEach(line => {
        const lineContainer = document.querySelector(line.id);
        const lineElement = lineContainer.querySelector(".line");
    const targetLength = (line.targetNumber / 300) * lineContainer.clientWidth;
    
    tlp2.to(lineElement, {
      width: targetLength + 'px',
      duration: 2,
      ease: "power2.inOut"
    }, 0);
  
    tlp2.to({}, {
      duration: 2,
      onUpdate: function() {
        const progress = this.progress();
        const currentNumber = Math.floor(progress * line.targetNumber);
        document.querySelector(line.number).innerText = currentNumber;
      },
      ease: "power2.inOut"
    }, 0);
  });
  
  tlp2.to("#p2r3c2r2 #line1", { width: "calc(25% - 15px)" });
  tlp2.to("#p2t1", { opacity: 1, duration: 0.5 });
  tlp2.to("#p2t2", { opacity: 1, duration: 0.5 });
  tlp2.to("#p2r3c2r2 #line2", { height: "calc(100% - 50px)" }, "<");
  tlp2.to("#circle2", { visibility: "visible", scale: 1 });
  tlp2.to("#p2r3c2r2 #line3", { width: "calc(25% + 10px)" });
  tlp2.to("#p2r3c2r2 #line4", { height: "calc(100% - 50px)" });
  tlp2.to("#circle3", { visibility: "visible", scale: 1 });
  tlp2.to("#p2t3", { opacity: 1, duration: 0.5 }, "<");
  tlp2.to("#p2r3c2r2 #line5", { width: "calc(25% - 15px)" }, );
  tlp2.to("#p2t4", { opacity: 1, duration: 0.5 });
  tlp2.to("#circle4", { visibility: "visible", scale: 1 },"<");
  tlp2.to("#p2r3c2r2 #line6", { height: "calc(100% - 50px)" }, );
  tlp2.to("#p2t5", { opacity: 1, duration: 0.5 });
  tlp2.to("#p2r3c2r2 #line7", { width: "calc(25% - 15px)" }, '<');
  tlp2.to("#circle5", { visibility: "visible", scale: 1 });

  const pingzi = document.getElementById("p2r3c1r2");
      const page2 = document.getElementById("page2");

      pingzi.addEventListener("mouseenter", () => {
        // Hide first background image and show second
        gsap.to(pingzi, {
          duration: 1,
          backgroundImage: 'url("images/P2/top50adjs.png"), none',
          backgroundColor:"#fdf6ec"
        });

        // Move to the center of page2 and scale up
        const rect = pingzi.getBoundingClientRect();
        const containerX = rect.left + rect.width / 2;
        const containerY = rect.top + rect.height / 2;
        const page2X = window.innerWidth / 2;
        const page2Y = window.innerHeight / 2;

        page2.classList.add("show");
        gsap.to(pingzi, {
          duration: 1,
          zIndex:5,
          x: page2X - containerX,
          y: page2Y - containerY,
          scale: 3,
          ease: "power2.inOut",
          onComplete: () => {
            // Append the container to page2 after animation
            // page2.appendChild(container);
          },
        });
      });

      pingzi.addEventListener("mouseleave", () => {
        // Reset background image
        gsap.to(pingzi, {
          duration: 1,
          backgroundImage:
            'url("images/pingzi.png"), url("images/P2/top50adjs.png")',
        });

        // Move back to original position and scale down
        const rect = pingzi.getBoundingClientRect();
        const containerX = rect.left + rect.width / 2;
        const containerY = rect.top + rect.height / 2;
        const page2X = window.innerWidth / 2;
        const page2Y = window.innerHeight / 2;

        gsap.to(pingzi, {
          duration: 1,
          x: 0,
          y: 0,
          scale: 1,
          ease: "power2.inOut",
          onComplete: () => {
            // Remove the container from page2 after animation  
            // document.body.appendChild(container);
            page2.classList.remove("show");
          },
        });
            })
                }}
</script>

<style scoped>
@import '../assets/style/P2.css';
@import '../assets/style/style.css';

</style>
  