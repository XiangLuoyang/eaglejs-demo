<template lang="pug">
eg-transition(:enter='enter', :leave='leave')
  .eg-slide(v-if='active')
    .eg-slide-content
      h3.center(v-if='step < 12') 出行特征可视化
      h3.center(v-else) Slideception !!


      eg-transition(enter='bounceInLeft' leave='bounceOutLeft')
        .subslide(v-if='step <= 2')
          p.center
            |客流出行特征的三个维度：时间、距离、次数
          eg-code-block(lang='html', v-if="step <= 2").
            1. 客流特征关联
            2. 平均出行次数
            3. 片区平均停留时间轴
            4. 平均出行距离频率分布
            5. 平均出行时间分布
            6. 房价空间
          br
          eg-transition(enter='fadeIn')
            .center
              img.shadowbox(v-if='step <= 2',src='./assets/chuxingtezheng.png' width='300px' height='300px')
      eg-transition(enter='bounceInRight')
        .subslide(v-if='(step >= 3) && (step < 8)')
          p.center(v-if='(3 <= step) && (step <= 4)')
             |关于特征关联的描述
          .center
            img.shadowbox(style='width:720px;height:417px' v-if='(4 <= step) && (step < 5)' src = '/static/城市轨道交通客流出行特征关联可视化.png')
          p.center(v-if='(5 <= step) && (step < 8)')
             |关于平均出行特征的描述
          //- 插入图表的ppt
          eg-transition(v-if='(5 <= step) && (step < 8)')
            #awesome-slideshow.embedded-slideshow-container(v-if='(5 <= step) && (step < 8)')
              awesome-embedded-slideshow(:embedded='true', :username='username',
                                         :preference='preference')
      eg-transition(v-if='step >= 7' enter='bounceInUp' leave='bounceOutUp')
        .subslide(v-if='(step >= 8) && (step < 15)' enter = 'fadeIn')
          p.center(v-if='step >= 8')
            |关于房价空间可视化的描述
          .center
            img.shadowbox(style='width:720px;height:417px' v-if='step === 8' src = '/static/城市区域热力图.jpg')
</template>

<script>
import AwesomeEmbeddedSlideshow from './AwesomeEmbeddedSlideshow'
import eagle from 'eagle.js'
export default {
  props: {
    steps: {default: 8},
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
