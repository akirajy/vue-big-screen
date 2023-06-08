<template>
  <div>
    <div id="centreLeft2Chart" style="width:330px; height: 370px;"></div>
  </div>
</template>

<script>
const echarts = require("echarts");
export default {
  data() {
    return {};
  },
  mounted() {
    this.drawPie();
  },
  methods: {
    drawPie(sidebar) {
      // 基于准备好的dom，初始化echarts实例
      let myChartPieLeft = echarts.init(
        document.getElementById("centreLeft2Chart")
      );
      //  ----------------------------------------------------------------

      let option = {
        angleAxis: {
          interval: 1,
          type: "category",
          data: ['0°-30°', '30°-60°', '60°-90°', '90°-120°', '120°-150°', '150°-180°', '180°-210°', '210°-240°', '240°-270°', '270°-300°', '300°-330°', '330°-360°'],
          z: 10,
          axisLine: {
            show: true,
            lineStyle: {
              color: "#00c7ff",
              width: 1,
              type: "solid"
            }
          },
          axisLabel: {
            interval: 0,
            show: true,
            color: "#00c7ff",
            margin: 8,
            fontSize: 12
          }
        },
        radiusAxis: {
          min: 0,
          max: 100,
          interval: 20,
          axisLine: {
            show: true,
            lineStyle: {
              color: "#00c7ff",
              width: 1,
              type: "solid"
            }
          },
          axisLabel: {
            formatter: "{value} %",
            show: false,
            padding: [0, 0, 20, 0],
            color: "#00c7ff",
            fontSize: 16
          },
          splitLine: {
            lineStyle: {
              color: "#00c7ff",
              width: 1,
              type: "solid"
            }
          }
        },
        legend: {
          show: true,
          orient: "vartical",
          top: "center",
          bottom: "0%",
          itemWidth: 16,
          itemHeight: 8,
          itemGap: 16,
          textStyle: {
            color: "#A3E2F4",
            fontSize: 12,
            fontWeight: 0
          },
          data: ["A"]
        },
        polar: {},
        series: [
          {
            name: "A",
            type: "bar",
            radius: ["20%", "100%"],
            data: [
              {
                value: 22.3,
                itemStyle: {
                  normal: {
                    color: "#f54d4d"
                  }
                }
              },
              {
                value: 4.5,
                itemStyle: {
                  normal: {
                    color: "#f87544"
                  }
                }
              },
              {
                value: 88.0,
                itemStyle: {
                  normal: {
                    color: "#ffae00"
                  }
                }
              },
              {
                value: 89.2,
                itemStyle: {
                  normal: {
                    color: "#dcff00"
                  }
                }
              },
              {
                value: 25.8,
                itemStyle: {
                  normal: {
                    color: "#25d053"
                  }
                }
              },
              {
                value: 135.4,
                itemStyle: {
                  normal: {
                    color: "#01fff5"
                  }
                }
              },
              {
                value: 77.6,
                itemStyle: {
                  normal: {
                    color: "#007cff"
                  }
                }
              },
              {
                value: 18.7,
                itemStyle: {
                  normal: {
                    color: "#4245ff"
                  }
                }
              },
              {
                value: 19.5,
                itemStyle: {
                  normal: {
                    color: "#c32eff"
                  }
                }
              },
              {
                value: 56.2,
                itemStyle: {
                  normal: {
                    color: "#ff62e8"
                  }
                }
              },
              {
                value: 19.6,
                itemStyle: {
                  normal: {
                    color: "#db35b5"
                  }
                }
              },
              {
                value: 148.9,
                itemStyle: {
                  normal: {
                    color: "#7351a0"
                  }
                }
              }
            ],
            coordinateSystem: "polar"
          }
        ]
      };
      myChartPieLeft.setOption(option);
      // -----------------------------------------------------------------
      // 响应式变化
      window.addEventListener("resize", () => myChartPieLeft.resize(), false);
      //侧边栏变化
      if (sidebar) {
        myChartPieLeft.resize();
      }
    }
  },
  destroyed() {
    window.onresize = null;
  }
};
</script>

<style lang="scss" scoped>
</style>