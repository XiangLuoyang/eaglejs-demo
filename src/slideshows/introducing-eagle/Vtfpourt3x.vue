<template lang="pug">
eg-transition(:enter='enter', :leave='leave')
  .eg-slide(v-if='active')
    .eg-slide-content
      h3(v-if='step <= 3') 客流分析可视化
      h3(v-if='(step > 3) && (step <= 12)') 类别
      h3(v-if='(step > 12) && (step <= 13)') 时间
      h3(v-if='step > 13') 空间


      eg-transition(leave='bounceOutLeft')
        .subslide(v-if='step <= 3')
          p.
          .center
            |基于三个维度：类别、时间、空间
          br
          br
          eg-code-block(lang='html', v-if="step <= 3").
            1. 轨道站点高峰小时内进站客流变化<b>趋势</b>折线图
            2. 轨道典型站点客流进/出站<b>流量</b>金字塔图/漏斗图
            3. 轨道站点日均客运量<b>比重</b>分布南丁格尔玫瑰图
            4. 轨道站点<b>流量流向</b>分布和弦图
            5. 各轨道线路日均进站量及日均客运量<b>排名</b>条状图 <eg-code-comment :active='step === 2' enter='flipInY'> 基于类别分布，我们可以对客流出行的这些方面进行分析</eg-code-comment>
            6. 轨道线路<b>客流OD</b>分布桑基图
            7. 轨道站点日均<b>客流量</b>分布矩阵树图
            8. 各行政区轨道进客站客流总量<b>排行榜</b>条状图
            9. 各功能区轨道线路<b>流量极差</b>分布气泡图

          eg-transition(enter='fadeIn')
            p(v-if='step === 3').
              密密麻麻的字，正好体现了数据可视化的优点
      eg-transition(enter='bounceInRight')
        .subslide(v-if='(step >= 4) && (step < 13)')

          p(v-if='(3 <= step) && (step < 6)' style='margin-left:20%')
             | You:
             span(v-if='(4 <= step) && (step < 6)') &nbsp; 讲那么多，记不住有什么用?
          p(v-if='(6 <= step) && (step <= steps)' style='margin-left:20%') You: 然后呢？
          eg-transition(enter='fadeIn')
            #awesome-slideshow.embedded-slideshow-container(v-if='step >= 5')
              vtfpourt3xEmbedded(:embedded='true', :username='username',
                                         :preference='preference')
          eg-transition(enter='slideInUp')
            p(v-if='(11 < step)  && (step <= 12)').
              If you lost track: you are watching a slideshow embedded
              in a slideshow embedded in a slide inserted in a slideshow.

      eg-transition(enter='bounceInRight')
        .subslide(v-if='(step >= 13) && (step < 14)')
          p.center(v-if='(13 <= step) && (step < 14)')
             | You:
             span(v-if='(13 <= step) && (step < 14)') &nbsp; 那基于时间和空间呢
          .center
            img.shadowbox(src='/static/轨道交通客流分析时间维度.png' style="width:1200px;max-width:100%;")
        .subslide(v-if='(step >= 14) && (step < 16)')
          p.center(v-if='(14 <= step) && (step < 15)')
             | You:
             span(v-if='(14 <= step) && (step < 15)') &nbsp; 那空间也想必差不多吧
          eg-transition(enter='bounceInLeft')
            .center
              img.shadowbox(src='/static/轨道交通客流分析空间维度.png' style="width:1200px;max-width:100%;")
</template>

<script>
import Vtfpourt3xEmbedded from './Vtfpourt3xEmbedded'
import eagle from 'eagle.js'
export default {
  props: {
    steps: {default: 14},
    username: {default: 'Tracy'},
    preference: {default: 'baby bunnies'}
  },
  components: {
    'vtfpourt3xEmbedded': Vtfpourt3xEmbedded
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
