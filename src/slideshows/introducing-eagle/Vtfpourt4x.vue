<template lang="pug">
eg-transition(:enter='enter', :leave='leave')
  .eg-slide(v-if='active')
    .eg-slide-content
      h3(v-if='step < 12') 城市轨道交通客流移动轨迹可视化
      h3(v-else) Slideception !!
      eg-transition(leave='bounceOutLeft')
        .subslide(v-if='step <= 2')
          p.
          .center
            |基于三种方式：直接可视化、聚集可视化、特征可视化
          br
          br
          eg-code-block(lang='html', v-if="step === 2").
            1. 这一整章的内容说的都是之前提到的关键词之一：轨迹
            2. 关于移动轨迹可视化的方式有很多。我们先分情况讨论有哪些作图环境和条件
            3. 讨论一下在不同的环境和条件下选用什么样的图

          eg-transition(enter='fadeIn')
            p(v-if='step === 2').
              直接可视化的介绍可以一笔带过，最多配合一张描绘上轨迹的地图
      eg-transition(enter='bounceInRight')
        .subslide(v-if='(step >= 4) && (step < 15)')

          p(v-if='(3 <= step) && (step < 6)')
             | You: 这里放入聚集可视化的类型，划分依据，比如SS、STA、R等
             span(v-if='(4 <= step) && (step < 6)') &nbsp; S、T、A、R分别代表什么?
          p(v-if='(6 <= step) && (step <= steps)') You: 还有什么图？

          eg-transition(enter='lightSpeedIn')
            #awesome-slideshow.embedded-slideshow-container(v-if='step >= 5')
              awesome-embedded-slideshow(:embedded='true', :username='username',
                                         :preference='preference')
          eg-transition(enter='slideInUp')
            p(v-if='(11 < step)  && (step <= 13)').
              这里可以放入特征可视化的类型、典型案例，图等
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
