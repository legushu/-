<template>
  <div id="container" style="height: 100vh;">
    <el-container>
<!--      <el-header>-->
<!--        -->
<!--        <div class="title"></div>-->
<!--      </el-header>-->

      <el-main>
        <el-image
          style="margin-left: 600px;height: 200px;"
          :src="require('../assets/png/item2.png')"
          fit="cover"></el-image>
        <div class="title-lg">数读唐诗三百首，览尽诗意岁月长</div>
        <div class="sub-title">——基于唐诗的可视化分析</div>
        <div class="grid">
          <div class="desc">唐诗，是中华文化宝库中的一颗明珠，同时也对当今中国人的生活，以及世界上许多国家的文化发展产生了很大影响，对于后人研究唐代的政治、民情、风俗、文化等都具有重要的参考意义。
            <br>在我们的可视化项目中，我们将从不同的维度分析来自《唐诗三百首》的唐诗。通过分析唐诗文本，用户可以通过可视化的方式了解诗人的生平以及唐朝国家实力与社会风气的变化。同时，通过分析各种诗歌意象，用户可以直观地了解到诗歌意象与主题情感的联系，同时展示古代的诗歌如何对今天人类的生活产生深远的影响。
          </div>
        </div>
        <div class="row">
          <el-row :gutter="10">
            <el-col :span="6">
              <div class="grid">
                <div class="desc-sm">“草木皆有情，词即人生。”<br><br>唐代在玄宗年间由盛转衰，处在不同年代的诗人，也有了不同的人生基调，我们不仅可以透过唐诗中的词语，看到唐代诗人的内心情感，还可以看到他们的人生经历，再向更广的纬度延展，我们也能够看到朝代的浪潮如何吹拂过生命的浮沉。</div>
                <el-image
                  style="margin-top: 30px;height: 100px;"
                  :src="require('../assets/png/item1.png')"
                  fit="contain"></el-image>
              </div>
            </el-col>
            <el-col :span="18">
              <el-radio v-model="radio1" label="1">全本</el-radio>
              <el-radio v-model="radio1" label="2">按风格</el-radio>
              <el-radio v-model="radio1" label="3">按诗人</el-radio>
              <div class="content" v-if="radio1==='1'">
                <el-image
                  style="height: 500px"
                  :src="require('../assets/png/word.png')"
                  fit="contain"></el-image>
              </div>
              <div class="content" v-if="radio1==='2'">
                <el-row :gutter="10">
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/word-cls1.png')"
                        fit="contain"></el-image>
                      <div class="title">咏物诗</div>
                    </div>
                  </el-col>
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/word-cls2.png')"
                        fit="contain"></el-image>
                      <div class="title">叙事诗</div>
                    </div>
                  </el-col>
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/word-cls3.png')"
                        fit="contain"></el-image>
                      <div class="title">山水田园诗</div>
                    </div>
                  </el-col>
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/word-cls4.png')"
                        fit="contain"></el-image>
                      <div class="title">边塞诗</div>
                    </div>
                  </el-col>
                </el-row>
                <el-row :gutter="10">
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/word-cls5.png')"
                        fit="contain"></el-image>
                      <div class="title">离别诗</div>
                    </div>
                  </el-col>
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/word-cls6.png')"
                        fit="contain"></el-image>
                      <div class="title">爱情诗</div>
                    </div>
                  </el-col>
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/word-cls7.png')"
                        fit="contain"></el-image>
                      <div class="title">咏怀咏史诗</div>
                    </div>
                  </el-col>
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/word-cls8.png')"
                        fit="contain"></el-image>
                      <div class="title">酬唱诗</div>
                    </div>
                  </el-col>
                </el-row>
              </div>
              <div class="content" v-if="radio1==='3'">
                <el-row :gutter="10">
                  <el-col :span="8">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/word-author1.png')"
                        fit="contain"></el-image>
                      <el-popover
                        placement="top-start"
                        width="200"
                        trigger="hover">
                        <div class="title" slot="reference">李白</div>
                        <div class="popup">
                          <img :src="poets[0].paragraph">
                          <div class="popup-title">{{poets[0].author}}</div>
                          <div class="popup-content">{{poets[0].info}}</div>
                        </div>
                      </el-popover>
                    </div>
                  </el-col>
                  <el-col :span="8">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/word-author2.png')"
                        fit="contain"></el-image>
                      <el-popover
                        placement="top-start"
                        width="200"
                        trigger="hover">
                        <div class="title" slot="reference">王维</div>
                        <div class="popup">
                          <img :src="poets[2].paragraph">
                          <div class="popup-title">{{poets[2].author}}</div>
                          <div class="popup-content">{{poets[2].info}}</div>
                        </div>
                      </el-popover>
                    </div>
                  </el-col>
                  <el-col :span="8">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/word-author3.png')"
                        fit="contain"></el-image>
                      <el-popover
                        placement="top-start"
                        width="200"
                        trigger="hover">
                        <div class="title" slot="reference">杜甫</div>
                        <div class="popup">
                          <img :src="poets[4].paragraph">
                          <div class="popup-title">{{poets[4].author}}</div>
                          <div class="popup-content">{{poets[4].info}}</div>
                        </div>
                      </el-popover>
                    </div>
                  </el-col>
                </el-row>
                <el-row :gutter="10">
                  <el-col :span="8">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/word-author4.png')"
                        fit="contain"></el-image>
                      <el-popover
                        placement="top-start"
                        width="200"
                        trigger="hover">
                        <div class="title" slot="reference">李商隐</div>
                        <div class="popup">
                          <img :src="poets[5].paragraph">
                          <div class="popup-title">{{poets[5].author}}</div>
                          <div class="popup-content">{{poets[5].info}}</div>
                        </div>
                      </el-popover>
                    </div>
                  </el-col>
                  <el-col :span="8">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/word-author5.png')"
                        fit="contain"></el-image>
                      <el-popover
                        placement="top-start"
                        width="200"
                        trigger="hover">
                        <div class="title" slot="reference">孟浩然</div>
                        <div class="popup">
                          <img :src="poets[7].paragraph">
                          <div class="popup-title">{{poets[7].author}}</div>
                          <div class="popup-content">{{poets[7].info}}</div>
                        </div>
                      </el-popover>
                    </div>
                  </el-col>
                  <el-col :span="8">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/word-author6.png')"
                        fit="contain"></el-image>
                      <el-popover
                        placement="top-start"
                        width="200"
                        trigger="hover">
                        <div class="title" slot="reference">韦应物</div>
                        <div class="popup">
                          <img :src="poets[10].paragraph">
                          <div class="popup-title">{{poets[10].author}}</div>
                          <div class="popup-content">{{poets[10].info}}</div>
                        </div>
                      </el-popover>
                    </div>
                  </el-col>
                </el-row>
              </div>
              <el-row>
                <el-col :span="24">
                  <div class="legend">图1 《唐诗三百首》词频统计结果</div>
                </el-col>
              </el-row>
            </el-col>
          </el-row>
        </div>
        <div style="height: 50px"></div>
        <div class="row">
          <el-row :gutter="10">
            <el-col :span="18">
              <el-radio v-model="radio2" label="1">全本</el-radio>
              <el-radio v-model="radio2" label="2">按风格</el-radio>
              <el-radio v-model="radio2" label="3">按诗人</el-radio>
              <div class="content" v-if="radio2==='1'">
                <el-image
                  style="height: 500px"
                  :src="require('../assets/png/imagery.png')"
                  fit="contain"></el-image>
              </div>
              <div class="content" v-if="radio2==='3'">
                <el-row :gutter="10">
                  <el-col :span="8">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/imagery-author1.png')"
                        fit="contain"></el-image>
                      <el-popover
                        placement="top-start"
                        width="200"
                        trigger="hover">
                        <div class="title" slot="reference">李白</div>
                        <div class="popup">
                          <img :src="poets[0].paragraph">
                          <div class="popup-title">{{poets[0].author}}</div>
                          <div class="popup-content">{{poets[0].info}}</div>
                        </div>
                      </el-popover>
                    </div>
                  </el-col>
                  <el-col :span="8">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/imagery-author2.png')"
                        fit="contain"></el-image>
                      <el-popover
                        placement="top-start"
                        width="200"
                        trigger="hover">
                        <div class="title" slot="reference">王维</div>
                        <div class="popup">
                          <img :src="poets[2].paragraph">
                          <div class="popup-title">{{poets[2].author}}</div>
                          <div class="popup-content">{{poets[2].info}}</div>
                        </div>
                      </el-popover>
                    </div>
                  </el-col>
                  <el-col :span="8">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/imagery-author3.png')"
                        fit="contain"></el-image>
                      <el-popover
                        placement="top-start"
                        width="200"
                        trigger="hover">
                        <div class="title" slot="reference">杜甫</div>
                        <div class="popup">
                          <img :src="poets[4].paragraph">
                          <div class="popup-title">{{poets[4].author}}</div>
                          <div class="popup-content">{{poets[4].info}}</div>
                        </div>
                      </el-popover>
                    </div>
                  </el-col>
                </el-row>
                <el-row :gutter="10">
                  <el-col :span="8">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/imagery-author4.png')"
                        fit="contain"></el-image>
                      <el-popover
                        placement="top-start"
                        width="200"
                        trigger="hover">
                        <div class="title" slot="reference">李商隐</div>
                        <div class="popup">
                          <img :src="poets[5].paragraph">
                          <div class="popup-title">{{poets[5].author}}</div>
                          <div class="popup-content">{{poets[5].info}}</div>
                        </div>
                      </el-popover>
                    </div>
                  </el-col>
                  <el-col :span="8">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/imagery-author5.png')"
                        fit="contain"></el-image>
                      <el-popover
                        placement="top-start"
                        width="200"
                        trigger="hover">
                        <div class="title" slot="reference">孟浩然</div>
                        <div class="popup">
                          <img :src="poets[7].paragraph">
                          <div class="popup-title">{{poets[7].author}}</div>
                          <div class="popup-content">{{poets[7].info}}</div>
                        </div>
                      </el-popover>
                    </div>
                  </el-col>
                  <el-col :span="8">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/imagery-author6.png')"
                        fit="contain"></el-image>
                      <el-popover
                        placement="top-start"
                        width="200"
                        trigger="hover">
                        <div class="title" slot="reference">韦应物</div>
                        <div class="popup">
                          <img :src="poets[10].paragraph">
                          <div class="popup-title">{{poets[10].author}}</div>
                          <div class="popup-content">{{poets[10].info}}</div>
                        </div>
                      </el-popover>
                    </div>
                  </el-col>
                </el-row>
              </div>
              <div class="content" v-if="radio2==='2'">
                <el-row :gutter="10">
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/imagery-cls1.png')"
                        fit="contain"></el-image>
                      <div class="title">咏物诗</div>
                    </div>
                  </el-col>
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/imagery-cls2.png')"
                        fit="contain"></el-image>
                      <div class="title">叙事诗</div>
                    </div>
                  </el-col>
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/imagery-cls3.png')"
                        fit="contain"></el-image>
                      <div class="title">山水田园诗</div>
                    </div>
                  </el-col>
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/imagery-cls4.png')"
                        fit="contain"></el-image>
                      <div class="title">边塞诗</div>
                    </div>
                  </el-col>
                </el-row>
                <el-row :gutter="10">
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/imagery-cls5.png')"
                        fit="contain"></el-image>
                      <div class="title">离别诗</div>
                    </div>
                  </el-col>
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/imagery-cls6.png')"
                        fit="contain"></el-image>
                      <div class="title">爱情诗</div>
                    </div>
                  </el-col>
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/imagery-cls7.png')"
                        fit="contain"></el-image>
                      <div class="title">咏怀咏史诗</div>
                    </div>
                  </el-col>
                  <el-col :span="6">
                    <div class="grid-content">
                      <el-image
                        :src="require('../assets/png/imagery-cls8.png')"
                        fit="contain"></el-image>
                      <div class="title">酬唱诗</div>
                    </div>
                  </el-col>
                </el-row>

              </div>
              <el-row>
                <el-col :span="24">
                  <div class="legend">图2 《唐诗三百首》常见意象统计</div>
                </el-col>
              </el-row>
            </el-col>
            <el-col :span="6">
              <div class="desc-sm">“无我之境也。有我之境，以我观物，故物皆著我之色彩。无我之境，以物观物，故不知何者为我，何者为物。”<br><br>唐诗多工于运用意象，具有高超的借物抒怀水准。万水千山走遍，冷暖人情历尽，叩问本心才是诗人的真性情。因而诗人们常常沉思，有时还挟带着现世的种种忧愁，在山水草木之间，安放的是诗人们无处施展的情感。</div>
              <el-image
                style="margin-top: 30px;height: 100px;"
                :src="require('../assets/png/item1.png')"
                fit="contain"></el-image>
            </el-col>
          </el-row>

        </div>
        <div class="row">
          <el-row>
            <el-col :span="24">
              <div class="desc">境非独谓景物也，喜怒哀乐亦人心中之一境界。故能写真景物真感情者，谓之有境界。否则谓之无境界。<br>——王国维《人间词话》</div>
            </el-col>
          </el-row>
        </div>
        <div class="row">
          <el-row>
            <el-col :span="24">
              <div style="width: auto;height: 400px" id="sheet-3"></div>
            </el-col>
          </el-row>
        </div>
        <div class="row">
          <el-row>
            <el-col :span="24">
              <div class="desc">诗人对宇宙人生，须入乎其内，又须出乎其外。入乎其内，故能写之；出乎其外，故能观之。入乎其内，故有生气；出乎其外，故有高致。美成能入而不能出，白石以降，于此二事皆未梦见。<br>——王国维《人间词话》</div>
            </el-col>
          </el-row>
        </div>
        <div class="row">
          <el-row>
            <el-col :span="24">
              <div style="width: 100%;height: 400px" id="sheet-4"></div>
            </el-col>
          </el-row>
        </div>
        <el-image
          style="height: 100px;right: 0;"
          :src="require('../assets/png/item3.png')"
          fit="cover"></el-image>
      </el-main>
    </el-container>
  </div>
</template>

<style scoped>
.desc{
  font-size: 18px;
  line-height: 30px;
  margin: 100px;
}
.title{
  font-weight: bold;
  text-align: center;
  font-size: 20px;
  line-height: 30px;
  background-image: url("/src/assets/png/border.png");
}

#container {
  height: 100%;
  width: 100%;
  font-family: "SimSun", fangsong;
}

.el-header {
  background-color: #fef8ef;
  color: #cc9966;
  text-align: center;
}

.title-lg {
  margin-top: 50px;
  line-height: 60px;
  font-size: 40px;
  font-weight: bolder;
}
.sub-title{
  font-size: 30px;
  line-height: 40px;
}
.popup{
  font-family: "SimSun", fangsong;
}
.popup-title{
  font-weight: bold;
}

.popup-content{
}
.desc-sm{
  font-size: 18px;
  line-height: 30px;
}

.el-main {
  background-color: #fef8ef;
  color: #333;
  text-align: center;
  line-height: 100%;
}
.row {
  margin-top:20px;
  margin-bottom:20px;
}

.grid-content {
  /*background: #ffffff00;*/
  border-radius: 4px;
  background-color: transparent;
  min-height: 36px;
  margin-top: 5px;
  margin-bottom: 5px;
  line-height: 100%;
}
.legend{
  font-weight: bolder;
  font-size: 15px;
}
.content{
  height: 500px;
  margin-top: 30px;
  margin-bottom: 30px;
}
</style>

<script>
import axios from "axios";

require("echarts/theme/vintage")

export default {
  name: 'App',
  data() {
    return {
      radio1: '1',
      radio2: '1',
      poets: [],
      links3: [],
      links4: []
    }
  },
  mounted() {
    axios('api/source_and_target').then(res=>{
      this.links3=res.data
      this.sheet3()
    })
    axios('api/time_poet_Classification').then(res=>{
      this.links4=res.data
      this.sheet4()
    })
    axios('api/poet5').then(res=>{
      this.poets=res.data
    })
    this.sheet4();
  },
  methods: {
    sheet4() {
      var myChart = this.$echarts.init(document.getElementById('sheet-4'), 'vintage');
      var option = {
        title: {
          text: '诗人，所处时期与情感的对应',
          left:'4%',
          textStyle: {
            fontFamily: "SimSun"
          },
        },
        tooltip: {
          show:"true"
        },
        series: {
          type: 'sankey',
          layout: 'none',
          emphasis: {
            focus: 'adjacency'
          },
          data: [
            {
              name: '盛唐'
            },
            {
              name: '中唐'
            },
            {
              name: '晚唐'
            },
            {
              name: '咏物诗'
            },
            {
              name: '叙事诗'
            },
            {
              name: '山水田园诗'
            },
            {
              name: '边塞诗'
            },
            {
              name: '离别诗'
            },
            {
              name: '爱情诗'
            },
            {
              name: '咏怀咏史诗'
            },
            {
              name: '酬唱诗'
            },
            {
              name: '李白'
            }, {
              name: '王维'
            }, {
              name: '杜甫'
            }, {
              name: '李商隐'
            }, {
              name: '孟浩然'
            }, {
              name: '韦应物'
            }, {
              name: '岑参'
            }, {
              name: '白居易'
            }, {
              name: '杜牧'
            }, {
              name: '王昌龄'
            }, {
              name: '刘长卿'
            }, {
              name: '李颀'
            }
          ],
          links: this.links4
        }
      };
      myChart.setOption(option);
    },
    sheet3() {
      var myChart = this.$echarts.init(document.getElementById('sheet-3'), 'vintage');
      var option = {
        title: {
          text: '诗歌体裁与情感的对应',
          left:'4%',
          textStyle: {
            fontFamily: "SimSun"
          },
        },
        tooltip: {
          show:"true"
        },
        series: {
          type: 'sankey',
          layout: 'none',
          emphasis: {
            focus: 'adjacency'
          },
          data: [
            {
              name: '五言古体诗'
            },
            {
              name: '七言古体诗'
            },
            {
              name: '五言绝句'
            },
            {
              name: '七言绝句'
            },
            {
              name: '五言律诗'
            },
            {
              name: '七言律诗'
            },
            {
              name: '咏物诗'
            },
            {
              name: '叙事诗'
            },
            {
              name: '山水田园诗'
            },
            {
              name: '边塞诗'
            },
            {
              name: '离别诗'
            },
            {
              name: '爱情诗'
            },
            {
              name: '咏怀咏史诗'
            },
            {
              name: '酬唱诗'
            }
          ],
          links: this.links3
        }
      };
      myChart.setOption(option);
    }
  }
}
</script>
