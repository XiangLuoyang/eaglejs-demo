<template lang="pug">
eg-transition(:enter='enter', :leave='leave')
  .eg-slide(v-if='active')
    .eg-slide-content
      h3(v-if='step < 12') 城市轨道交通客流出行特征可视化
      h3(v-else) Slideception !!


      eg-transition(leave='bounceOutLeft')
        .subslide(v-if='step <= 2')
          p.
          .center
            |客流出行特征的三个维度：时间、距离、次数

          eg-code-block(lang='html', v-if="step === 2").
            1. 客流特征关联
            2. 平均出行次数
            3. 片区平均停留时间轴
            4. 平均出行距离频率分布
            5. 平均出行时间分布
            6. 房价空间

          eg-transition(enter='fadeIn')
            p(v-if='step === 2').
              上面左边讲的是类别，右边可以放这些图是怎么选出来的过程
      eg-transition(enter='bounceInRight')
        .subslide(v-if='(step >= 4) && (step < 15)')

          p(v-if='(3 <= step) && (step < 6)')
             | You: W这里放入像embedded slide 的图，图<i>不要</i>在公司里画，画出上面几个轨道站点图片的生成过程 ?
             span(v-if='(4 <= step) && (step < 6)') &nbsp; How is this slide <i>complex</i>?
          p(v-if='(6 <= step) && (step <= steps)') You: 还有什么图？

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
