<template lang="pug">
eg-transition(:enter='enter', :leave='leave')
  .eg-slide(v-if='active')
    .eg-slide-content
      h3(v-if='step < 12') 城市轨道交通网络客流分析可视化
      h3(v-else) Slideception !!


      eg-transition(leave='bounceOutLeft')
        .subslide(v-if='step <= 2')
          p.
          .center
            |基于三个维度：类别、时间、空间

          eg-code-block(lang='html', v-if="step === 2").
            1. 轨道站点高峰小时内进站客流变化<b>趋势</b>折线图
            2. 轨道典型站点客流进/出站<b>流量</b>金字塔图/漏斗图
            3. 轨道站点日均客运量<b>比重</b>分布南丁格尔玫瑰图
            4. 轨道站点<b>流量流向</b>分布和弦图
            5. 各轨道线路日均进站量及日均客运量<b>排名</b>条状图
            6. 轨道线路<b>客流OD</b>分布桑基图
            7. 轨道站点日均<b>客流量</b>分布矩阵树图
            8. 各行政区轨道进客站客流总量<b>排行榜</b>条状图
            9. 各功能区轨道线路<b>流量极差</b>分布气泡图

          eg-transition(enter='fadeIn')
            p(v-if='step === 2').
              上面左边讲的是类别，右边可以放这些图是怎么选出来的过程
      eg-transition(enter='bounceInRight')
        .subslide(v-if='(step >= 4) && (step < 15)')

          p(v-if='(3 <= step) && (step < 6)')
             | You: W这里放入像embedded slide 的图，图<i>不要</i>在公司里画，画出上面几个轨道站点图片的生成过程 ?
             span(v-if='(4 <= step) && (step < 6)') &nbsp; How is this slide <i>complex</i>?
          p(v-if='(6 <= step) && (step <= steps)') You: ...

          eg-transition(enter='lightSpeedIn')
            #awesome-slideshow.embedded-slideshow-container(v-if='step >= 5')
              awesome-embedded-slideshow(:embedded='true', :username='username',
                                         :preference='preference')
          eg-transition(enter='slideInUp')
            p(v-if='(11 < step)  && (step <= 13)').
              If you lost track: you are watching a slideshow embedded
              in a slideshow embedded in a slide inserted in a slideshow.
</template>

<script>
import AwesomeEmbeddedSlideshow from './AwesomeEmbeddedSlideshow'
import eagle from 'eagle.js'
export default {
  props: {
    steps: {default: 14},
    username: {default: 'Tracy'},
    preference: {default: 'baby bunnies'}
  },
  components: {
    'awesome-embedded-slideshow': AwesomeEmbeddedSlideshow
  },
  mixins: [eagle.slide]
}
</script>
<style lang='scss' scoped>
.eg-slide {
  .eg-slide-content {
    .chuckle {
      color: grey;
      font-size: 0.6em;
      margin-right: 0.5em;
    }

    #awesome-slideshow {
      position: relative;
      margin: 0 auto;
      width: 16em;
      height: 9em;
    }

  }
}
</style>
