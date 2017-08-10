<template lang="pug">
eg-transition(:enter='enter', :leave='leave')
  .eg-slide(v-if='active')
    .eg-slide-content
      h3(v-if='step < 12') 客流类别可视化
      h3(v-else) Slideception !!
      eg-transition(leave='bounceOutLeft')
        .subslide(v-if='step <= 2')
          p.center(v-if='step === 1')
            |依据K-means聚类的客流类别划分
          p.center(v-if='step === 2')
            |2个大的方向和5个小的方向：正常出行/小众出行
          eg-transition(enter='bounceInDown' leave='bounceOutUp')
            eg-code-block(lang='html', v-if="step === 2").
              1. 客流类别比例分布
              2. 客流类别空间分布
              3. 通勤出行可视化
              4. 异常出行客流空间分布

          eg-transition(enter='fadeIn' leave='fadeOut')
            p(v-if='step === 2').
            .center
              img.computerkid.shadowbox(style='height:580px' src='static/客流类别划分.png')
      eg-transition(enter='bounceInRight')
        .subslide(v-if='(step >= 4) && (step < 15)')

          p(v-if='(3 <= step) && (step < 6)')
             | You: 这不就回到了之前说的
             span(v-if='(4 <= step) && (step < 6)') &nbsp; 依据关键词选择作图方式?
          .center
            img.computerkid.shadowbox(style='height:580px' src='static/轨道交通客流类别可视化.png')

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
    steps: {default: 4},
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
