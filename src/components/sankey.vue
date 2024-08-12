<template>
    <div class="chart-container" ref="chart"></div>
  </template>
  
  <script>
  import * as echarts from 'echarts';
  
  export default {
    name: 'SankeyChart',
    mounted() {
      this.initChart();
    },
    methods: {
      initChart() {
        const chartDom = this.$refs.chart;
        const myChart = echarts.init(chartDom, 'white', { renderer: 'canvas' });
  
        const option = {
          animation: true,
          animationThreshold: 2000,
          animationDuration: 1000,
          animationEasing: "cubicOut",
          animationDelay: 0,
          animationDurationUpdate: 300,
          animationEasingUpdate: "cubicOut",
          animationDelayUpdate: 0,
          aria: {
            enabled: false
          },
          color: [
            "#83bff6", // 淡蓝色
            "#96d2a1", // 淡绿色
            "#ffd700", // 金色
            "#ffa07a", // 淡粉色
            "#a0c4ff", // 淡紫色
            "#bada55", // 浅黄绿色
            "#f4a460", // 橙红色
            "#F7B52C", // 亮橙色
            "#FF950E"  // 橙黄色（数据量最大）
          ],
          series: [
            {
              type: "sankey",
              name: "流动数据",
              data: [
                { name: "广东省" },
                { name: "河南省" },
                { name: "广州市" },
                { name: "商丘市" },
                { name: "梅州市" },
                { name: "潮州市" },
                { name: "佛山市" },
                { name: "荔湾区" },
                { name: "黄埔区" },
                { name: "海珠区" },
                { name: "白云区" },
                { name: "天河区" },
                { name: "增城区" },
                { name: "禺城区" },
                { name: "大埔县" },
                { name: "从化区" },
                { name: "越秀区" },
                { name: "遂平县" },
                { name: "三水区" },
                { name: "番禺区" },
                { name: "南沙区" },
                { name: "潮安区" }
              ],
              links: [
                { source: "广东省", target: "佛山市", value: 1 },
                { source: "佛山市", target: "三水区", value: 1 },
                { source: "广东省", target: "广州市", value: 2 },
                { source: "广州市", target: "从化区", value: 2 },
                { source: "广东省", target: "广州市", value: 1 },
                { source: "广州市", target: "南沙区", value: 1 },
                { source: "广东省", target: "广州市", value: 3 },
                { source: "广州市", target: "增城区", value: 3 },
                { source: "广东省", target: "广州市", value: 5 },
                { source: "广州市", target: "天河区", value: 5 },
                { source: "广东省", target: "广州市", value: 12 },
                { source: "广州市", target: "海珠区", value: 12 },
                { source: "广东省", target: "广州市", value: 5 },
                { source: "广州市", target: "番禺区", value: 5 },
                { source: "广东省", target: "广州市", value: 7 },
                { source: "广州市", target: "白云区", value: 7 },
                { source: "广东省", target: "广州市", value: 27 },
                { source: "广州市", target: "荔湾区", value: 27 },
                { source: "广东省", target: "广州市", value: 5 },
                { source: "广州市", target: "越秀区", value: 5 },
                { source: "广东省", target: "广州市", value: 3 },
                { source: "广州市", target: "黄埔区", value: 3 },
                { source: "广东省", target: "梅州市", value: 1 },
                { source: "梅州市", target: "大埔县", value: 1 },
                { source: "广东省", target: "潮州市", value: 1 },
                { source: "潮州市", target: "潮安区", value: 1 },
                { source: "广东省", target: "潮州市", value: 1 },
                { source: "潮州市", target: "遂平县", value: 1 },
                { source: "河南省", target: "商丘市", value: 1 },
                { source: "商丘市", target: "禺城区", value: 1 }
              ],
              left: "0%",
              top: "0%",
              right: "10%",
              bottom: "50px",
              nodeWidth: 10,
              nodeGap: 8,
              nodeAlign: "justify",
              orient: "horizontal",
              draggable: true,
              label: {
                show: true,
                margin: 8,
              },
              lineStyle: {
                show: true,
                width: 1,
                opacity: 0.2,
                curveness: 0.5,
                type: "solid",
                color: "source"
              }
            }
          ],
        //   legend: [
        //     {
        //       data: ["流动数据"],
        //       selected: {},
        //       show: true,
        //       padding: 5,
        //       itemGap: 10,
        //       itemWidth: 25,
        //       itemHeight: 14,
        //       backgroundColor: "transparent",
        //       borderColor: "#ccc",
        //       borderRadius: 0,
        //       pageButtonItemGap: 5,
        //       pageButtonPosition: "end",
        //       pageFormatter: "{current}/{total}",
        //       pageIconColor: "#2f4554",
        //       pageIconInactiveColor: "#aaa",
        //       pageIconSize: 15,
        //       animationDurationUpdate: 800,
        //       selector: false,
        //       selectorPosition: "auto",
        //       selectorItemGap: 7,
        //       selectorButtonGap: 10
        //     }
        //   ],
          tooltip: {
            show: true,
            trigger: "item",
            triggerOn: "mousemove|click",
            axisPointer: {
              type: "line"
            },
            showContent: true,
            alwaysShowContent: false,
            showDelay: 0,
            hideDelay: 100,
            enterable: false,
            confine: false,
            appendToBody: false,
            transitionDuration: 0.4,
            textStyle: {
              fontSize: 14
            },
            borderWidth: 0,
            padding: 5,
            order: "seriesAsc"
          },
          title: [
            {
              show: false,
              text: "广彩相关企业地区分布桑基图",
              target: "blank",
              subtarget: "blank",
              padding: 5,
              itemGap: 10,
              textAlign: "auto",
              textVerticalAlign: "auto",
              triggerEvent: false
            }
          ]
        };
  
        myChart.setOption(option);
      }
    }
  };
  </script>
  
  <style scoped>
  .chart-container {
    position: relative;
    /* width: 100%;
    height: 100%; */
  }
  </style>