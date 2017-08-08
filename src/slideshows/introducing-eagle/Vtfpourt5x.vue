<template lang="pug">
eg-transition(:enter='enter', :leave='leave')
  .eg-slide(v-if='active')
    .eg-slide-content
      h3.center(v-if='step < 12') 出行特征可视化
      h3.center(v-else) Slideception !!


      eg-transition(leave='bounceOutLeft')
        .subslide(v-if='step <= 2')
          p.center
            |客流出行特征的三个维度：时间、距离、次数
          eg-code-block(lang='html', v-if="step === 2").
            1. 客流特征关联
            2. 平均出行次数
            3. 片区平均停留时间轴
            4. 平均出行距离频率分布
            5. 平均出行时间分布
            6. 房价空间
          br
          eg-transition(enter='fadeIn')
            img(v-if='step === 2',src='./assets/chuxingtezheng.png' style='margin-left:300px' width='300px' height='300px')
      eg-transition(enter='bounceInRight')
        .subslide(v-if='(step >= 3) && (step < 15)')
          p.center(v-if='(3 <= step) && (step <= 4)')
             |关于特征关联的描述
          img(style='margin-left:100px;width:720px;height:417px' v-if='(4 <= step) && (step < 5)' src = '/static/城市轨道交通客流出行特征关联可视化.png')
          p.center(v-if='(5 <= step) && (step < 8)')
             |关于平均出行特征的描述
          //- 插入图表的ppt
          eg-transition(v-if='(5 <= step) && (step < 8)')
            #awesome-slideshow.embedded-slideshow-container(v-if='(5 <= step) && (step < 8)')
              awesome-embedded-slideshow(:embedded='true', :username='username',
                                         :preference='preference')
          p.center(v-if='(8 <= step) && (step <= 9)')
             |关于房价空间可视化的描述
          eg-transition(enter='slideInUp')
            p(v-if='(9 < step)  && (step <= 10)').
              If you lost track: you are watching a slideshow embedded
              in a slideshow embedded in a slide inserted in a slideshow.
</template>

<script>
import AwesomeEmbeddedSlideshow from './AwesomeEmbeddedSlideshow'
import eagle from 'eagle.js'
export default {
  props: {
    steps: {default: 10},
    username: {default: 'Tracy'},
    preference: {default: 'baby bunnies'}
  },
  components: {
    'awesome-embedded-slideshow': AwesomeEmbeddedSlideshow,
    'figures-slide': require('./FiguresSlide')
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
