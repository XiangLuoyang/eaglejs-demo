<template lang="pug">
eg-transition(:enter='enter', :leave='leave')
  .eg-slide(v-if='active')
    .eg-slide-content
      h3(v-if='step <= 2') 移动轨迹可视化
      h4.center(v-if='(step >=3)&&(step <=5)') 直接可视化
      h4.center(v-if='(step >=6)&&(step <=15)') 聚集可视化
      h4.center(v-if='step >=15') 特征可视化
      eg-transition(leave='bounceOutLeft')
        .subslide(v-if='step <= 2')
          p.
          .center
            |基于三种方式：直接可视化、聚集可视化、特征可视化
          br
          eg-code-block(lang='html', v-if="step === 2").
            1. 这一整章的内容说的都是之前提到的关键词之一：轨迹
            2. 关于移动轨迹可视化的方式有很多。我们先分情况讨论有哪些作图环境和条件
            3. 讨论一下在不同的环境和条件下选用什么样的图
          br
          eg-transition(enter='fadeIn')
            img(v-if='step === 2',src='./assets/guijikeshihua.png' style='margin-left:100px')
      eg-transition(enter='bounceInRight')
        .subslide(v-if='(step >= 3) && (step < 15)')
          p.center(v-if='(3 <= step) && (step < 6)')
             | 直接可视化
             span(v-if='(4 <= step) && (step < 6)') &nbsp; 就很直接
          img(style='margin-left:100px' v-if='step === 5',src='./assets/zhijiekeshihua.png')

          p.center(v-if='(6 <= step) && (step < 9)')
             | 这里可以让DP出场，介绍聚集可视化的概念和图片
          p.center(v-if='(9 <= step) && (step <= 15)')
             | DP持续讲课时间

          eg-transition(enter='lightSpeedIn')
            #awesome-slideshow.embedded-slideshow-container(v-if='step >= 6')
              vtfpourt4xEmbedded(:embedded='true', :username='username',
                                         :preference='preference')

          eg-transition(enter='slideInUp')
            p(v-if='(11 < step)  && (step <= 15)').
              把上面那些兔子啊什么的换成雷达图什么的谢谢

</template>

<script>
import Vtfpourt4xEmbedded from './Vtfpourt4xEmbedded'
import eagle from 'eagle.js'
export default {
  props: {
    steps: {default: 14},
    username: {default: 'Tracy'},
    preference: {default: 'baby bunnies'}
  },
  components: {
    'vtfpourt4xEmbedded': Vtfpourt4xEmbedded
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
