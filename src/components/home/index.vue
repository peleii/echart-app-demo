<template>
  <div class="home-container">
    <div class="header">
      视频监控管理平台
    </div>
    <div class="main">
      <!-- <el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect">
        <el-menu-item index="1">处理中心</el-menu-item>
        <el-submenu index="2">
          <template slot="title">我的工作台</template>
          <el-menu-item index="2-1">选项1</el-menu-item>
          <el-menu-item index="2-2">选项2</el-menu-item>
          <el-menu-item index="2-3">选项3</el-menu-item>
        </el-submenu>
        <el-menu-item index="3" disabled>消息中心</el-menu-item>
        <el-menu-item index="4"><a href="https://www.ele.me" target="_blank">订单管理</a></el-menu-item>
      </el-menu> -->
      <div class="echarts">
        <div ref="echart1"></div>
        <div ref="echart2"></div>
        <div ref="echart3"></div>
        <div ref="echart4"></div>
      </div>
    </div>
  </div>
</template>

<script>
import * as echarts from 'echarts'
export default {
  name: 'home-index',
  data() {
    return {}
  },
  methods: {},
  mounted() {
    // 基于准备好的dom，初始化echarts实例
    console.log(this.$refs.echart1)
    var myChart1 = echarts.init(this.$refs.echart1)
    var myChart2 = echarts.init(this.$refs.echart2)
    // window.onresize = function () {
    //   myChart.resize()
    // }
    // // 绘制图表
    myChart1.setOption({
      title: {
        text: '设备数',
        left: '20px',
        top: '20px',
        textStyle: {
          color: '#FFF'
        }
      },
      tooltip: {},
      xAxis: {
        data: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23],
        type: 'category',
        nameTextStyle: {
          color: '#FFF'
        },
        axisLine: {
          lineStyle: {
            color: 'red'
          }
        }
      },
      yAxis: {
        type: 'value'
      },
      // 数据集，要展示的数据
      series: [
        // 第一组数据
        {
          name: 'A组',
          // type: 'bar',
          data: [20, 25, 28, 30, 33, 34, 36, 40, 44, 50, 58, 70, 82, 95, 90, 80, 68, 60, 48, 55, 65, 70, 75, 80],
          smooth: true,
          type: 'line',
          lineStyle: {
            normal: {
              color: 'green',
              width: 1,
              type: 'solid',
              shadowColor: 'green',
              shadowBlur: 20
            }
          },
          itemStyle: {
            normal: {
              opacity: 0
            }
          }
        },
        // 第二组数据
        {
          name: 'Bz组',
          // type: 'bar',
          data: [50, 65, 68, 70, 64, 50, 46, 40, 36, 28, 30, 32, 45, 55, 60, 70, 75, 60, 57, 55, 51, 49, 42, 50],
          smooth: true, // true为曲线
          type: 'line',
          // 折线样式
          lineStyle: {
            normal: {
              color: 'orange', // 折线颜色
              width: 1, // 折线宽度
              type: 'solid', // 折线线条类型
              shadowColor: 'orange', // 折线阴影颜色
              shadowBlur: 20 // 折线阴影大小
            }
          },
          // 数据点的样式
          itemStyle: {
            normal: {
              opacity: 0
            }
          }
        }
      ]
    })
    myChart2.setOption({
      title: {
        text: '近7天警告统计',
        left: '20px',
        top: '20px',
        textStyle: {
          color: '#FFF'
        }
      },
      tooltip: {
        trigger: 'item'
      },
      // 数据配色说明
      legend: {
        orient: 'vertical',
        x: '700px',
        y: '200px',
        data: ['A', 'B', 'C', 'D', 'E']
      },
      series: [
        {
          name: 'Access From',
          type: 'pie',
          radius: ['40%', '70%'],
          avoidLabelOverlap: false,
          label: {
            show: false,
            position: 'center',
            color: '#FFF'
          },
          emphasis: {
            label: {
              show: true,
              fontSize: '40',
              fontWeight: 'bold',
              color: '#FFF'
            }
          },
          labelLine: {
            show: false
          },
          data: [
            { value: 1048, name: 'A' },
            { value: 735, name: 'B' },
            { value: 580, name: 'C' },
            { value: 484, name: 'D' },
            { value: 300, name: 'E' }
          ]
        }
      ]
    })
  }
}
</script>

<style scoped lang='less'>
* {
  margin: 0;
  padding: 0;
}
.home-container {
  width: 1920px;
  margin: 0 auto;
  .header {
    background-image: url('@/assets/images/图层-3.png');
    background-repeat: no-repeat;
    text-align: center;
    width: 100%;
    height: 80px;
    line-height: 60px;
    color: #c3f8fe;
    background-size: cover;
    font-size: 30px;
  }
  .main {
    background-image: url('@/assets/images/shouye.jpg');
    background-repeat: no-repeat;
    background-position: top center;
    background-size: cover;
    width: 100%;
    height: 900px;
    margin-left: 2px;

    .echarts {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      div {
        width: 860px;
        height: 350px;
        background-image: url('@/assets/images/组-4.png');
        background-size: 860px 350px;
        background-repeat: no-repeat;
        // box-shadow: 10px 10px 5px #0054bd;

        margin: 50px 50px;
      }
    }
  }
}
</style>
