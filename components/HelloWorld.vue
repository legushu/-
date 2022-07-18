<template>
  <div id="container" style="height:100vh;">
    <el-container>
      <el-header>数读唐诗三百首</el-header>
      <el-main>
        <el-row :gutter="20">
          <el-col :span="9">
            <el-card :body-style="{ padding: '0px'}" shadow="hover">
              <el-carousel :autoplay="false">
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/worddf.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/worddm.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/wordlb.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/wordlcq.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/wordlsy.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/wordmhr.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/wordww.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/wordwyw.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
              </el-carousel>
              <div style="padding: 14px;">
                不同诗人的词频
              </div>
            </el-card>
            <el-card :body-style="{ padding: '0px'}" shadow="hover">
              <el-carousel autoplay="false">
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/word1.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/word2.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/word3.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/word4.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/word5.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
              </el-carousel>
              <div style="padding: 14px;">
                不同情感的词频
              </div>
            </el-card>
            <el-card :body-style="{ padding: '0px'}" shadow="hover">
              <el-carousel autoplay="false">
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/imagery1.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/imagery2.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/imagery2.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/imagery3.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/imagery4.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
                <el-carousel-item >
                  <el-image
                    :src="require('../assets/png/imagery5.png')"
                    fit="cover"></el-image>
                </el-carousel-item>
              </el-carousel>
              <div style="padding: 14px;">
                不同情感的意象
              </div>
            </el-card>
          </el-col>
          <el-col :span="15">
            <el-card :body-style="{ padding: '0px'}" shadow="hover">
              <div style="width: auto;height: 400px" id="main">
              </div>
            </el-card>
            <el-card :body-style="{ padding: '0px'}">
              <div style="width: auto;height: 400px" id="mainly"></div>
            </el-card>
          </el-col>
        </el-row>
      </el-main>
    </el-container>

  </div>
</template>
<script>
import axios from "axios";
require("echarts/theme/vintage")
export default {
  name: "HelloWorld",
  mounted() {
    axios('api/emotion').then(res=>{
      this.emotion=res.data
      for (let i = 0; i < res.data.length; i++) {
        res.data[i]
      }
    })
    axios('api/all_emotion').then(res=>{
      console.log(res.data)
      this.all_emotion=res.data
    })
    axios('api/poet').then(res=>{
      console.log(res.data)
      this.poet=res.data
    })
    this.myEcharts();
    this.mySanky();
  },
  methods:{
    mySanky(){
      var myChart = this.$echarts.init(document.getElementById('mainly'),'vintage');
      var option={
        series: {
          type: 'sankey',
          layout: 'none',
          emphasis: {
            focus: 'adjacency'
          },
          data: [
            {
              name: '李商隐'
            },
            {
              name: '白居易'
            },
            {
              name: '贾岛'
            },
            {
              name: '孟浩然'
            },
            {
              name: '李白'
            },
            {
              name: '王昌龄'
            },
            {
              name: '高适'
            },
            {
              name: '李申'
            },
            {
              name: '刘禹锡'
            },
            {
              name: '韦应物'
            },
            {
              name: '骆宾王'
            },
            {
              name: '韩愈'
            },
            {
              name: '张继'
            },
            {
              name: '较消极'
            },
            {
              name: '消极'
            },
            {
              name: '中性'
            },
            {
              name: '较积极'
            },
            {
              name: '积极'
            },
          ],
          links: [
            {
              source: '李商隐',
              target: '消极',
              value: 5
            },
            {
              source: '白居易',
              target: '较积极',
              value: 3
            },
            {
              source: '贾岛',
              target: '中性',
              value: 8
            },
            {
              source: '孟浩然',
              target: '积极',
              value: 3
            },
            {
              source: '李白',
              target: '积极',
              value: 1
            },
            {
              source: '王昌龄',
              target: '较积极',
              value: 2
            },
            {
              source: '高适',
              target: '较消极',
              value: 2
            },
            {
              source: '李申',
              target: '中性',
              value: 4
            },
            {
              source: '刘禹锡',
              target: '消极',
              value: 3
            },
            {
              source: '韦应物',
              target: '积极',
              value: 6
            },
            {
              source: '骆宾王',
              target: '积极',
              value: 4
            },
            {
              source: '韩愈',
              target: '较积极',
              value: 1
            },
            {
              source: '张继',
              target: '消极',
              value: 5
            },
          ]
        }
      };
      myChart.setOption(option);
    },
    myEcharts(){
      var myChart = this.$echarts.init(document.getElementById('main'),'vintage');
      //配置图表
      //
      var option={
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'line',
            lineStyle: {
              color: 'rgba(0,0,0,0.2)',
              width: 1,
              type: 'solid'
            }
          },
          formatter: function (params, ticket, callback) {
            htm=params[0].axisValue+'<br/>'
            for(var i=0;i<params.length;i++){
              htm=htm+(params[i].data[2]+params[i].data[1]+'<br/>')
            }
            return htm;
          }
        },
        legend: {
          data: ['消极', '较消极', '中性', '较积极', '积极']
        },
        singleAxis: {
          top: 50,
          bottom: 50,
          axisTick: {},
          axisLabel: {},
          data: ['初唐', '盛唐', '中唐', '晚唐'],
          type: 'category',
          axisPointer: {
            animation: true,
            label: {
              show: true
            }
          },
          splitLine: {
            show: true,
            lineStyle: {
              type: 'dashed',
              opacity: 0.2
            }
          }
        },
        series: [
          {
            type: 'themeRiver',
            emphasis: {
              itemStyle: {
                shadowBlur: 5,
                shadowColor: 'rgba(0, 0, 0, 0.5)'
              }
            },
            data: [
              ['0', 10, '消极'],//0是初唐，后面顺推
              ['1', 24, '消极'],
              ['2', 30, '消极'],
              ['3', 38, '消极'],

              ['0', 16, '较消极'],
              ['1', 15, '较消极'],
              ['2', 35, '较消极'],
              ['3', 8, '较消极'],

              ['0',20, '中性'],
              ['1', 5, '中性'],
              ['2', 45, '中性'],
              ['3', 48, '中性'],

              ['0', 49, '较积极'],
              ['1', 15, '较积极'],
              ['2', 35, '较积极'],
              ['3', 28, '较积极'],

              ['0', 10, '积极'],
              ['1', 15, '积极'],
              ['2', 25, '积极'],
              ['3', 38, '积极'],

            ]
          }
        ]
      };
      myChart.setOption(option);
    }
  },
  data() {
    return {
      emotion:[],
      poet: [],
      all_emotion: []
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#container {
  height: 100%;
  width: 100%;
  font-family:"SimSun",fangsong;
}

.grid-content {
  background: #d3dce6;
  border-radius: 4px;
  min-height: 36px;
  margin: 20px;
}

.el-header{
  background-color: #cccc99;
  color: #cc9966;
  text-align: left;
  line-height: 60px;
  font-size: 40px;
  font-weight: bolder;
}

.el-main {
  background-color: #ffffcc;
  color: #333;
  text-align: center;
  line-height: 100%;
}

.chart {
  height: 62.5vh;
}


.desc-content{
  font-size: 20px;
  padding: 14px;
  text-align: left;
}
.desc-content:first-letter{
  font-weight: bold;
}
.el-card{
  margin-bottom: 20px;
  border-radius: 10px;
  background-color: #fef8ef;
}
</style>
