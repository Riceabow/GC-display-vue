<template>  
    <div class="arch-bridge">  
      <!-- 圆弧部分将通过::before伪元素在CSS中定义 -->  
       <div class="arch-shade"></div>
    </div>  
  </template>  
    
  <script>  
  export default {  
    name: 'ArchBridge',  
    // 组件的其余部分（如props, data, methods等）可以根据需要添加  
  }  
  </script>  
    
  <style scoped>  
  .arch-bridge {  
    position: relative;  
    width: 100%; /* 长方形的宽度 */  
    height: 300px; /* 长方形的高度 */  
    background-color: #f19600; /* 长方形的背景色 */  
    overflow: hidden; /* 隐藏超出容器的部分 */  
  }  
    
  .arch-shade {  
    content: '';  
    position: absolute;  
    bottom: 0;  
    left: 50%;  
    top: 35%;
    width: 90%; /* 圆弧的宽度，小于长方形的宽度以创建镂空效果 */  
    height: 300%; /* 与长方形同高，但实际上我们会通过边框来创建圆弧 */  
    background-color:#fdf6ec; /* 圆弧的背景色，这里设为白色以模拟镂空效果 */  
    border-radius: 80% 80% 0 0; /* 仅顶部左右两个角设置圆角，模拟圆弧的顶部 */  
    transform: translateX(-50%); /* 居中圆弧 */  
  }  
  </style>