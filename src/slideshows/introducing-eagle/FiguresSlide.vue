<template lang="pug">
eg-transition(:enter='enter', :leave='leave')
  .eg-slide(v-if='active')
    .eg-slide-content
      eg-transition(enter='slideInRight', leave='fadeOutRight')
        .subslide(v-if='step ===1')
          p.center 平均出行次数
          .figure
            p.caption(v-html='title')
            chart(:data='figureData(step)', :options='figureOptions', type='doughnut',
                  :height='250')
      eg-transition(enter='slideInLeft', leave='fadeOutLeft')
        .subslide(v-if='step ===2')
          p.center 平均出行时间
          .figure
            p.caption(v-html='title')
            chart(:data='figureData(step)', :options='figureOptions', type='doughnut',
                  :height='250')
      eg-transition(enter='slideInRight', leave='fadeOutRight')
        .subslide(v-if='step ===3')
          p.center 平均出行距离
          .figure
            p.caption(v-html='title')
            chart(:data='figureData(step)', :options='figureOptions', type='doughnut',
                  :height='250')
</template>
<script>
import eagle from 'eagle.js'
import chart from './Chart'
export default {
  components: { chart },
  props: {
    steps: {default: 3}
  },
  data: function () {
    return {
      figureOptions: {
        legend: {
          display: false
        },
        animation: {
          duration: 1000
        }
      }
    }
  },
  computed: {
    title: function () {
      var line = '客流出行特征可视化'
      if (this.step === 1) {
        return line + '——平均出行次数'
      } else if (this.step === 2) {
        return line + '——平均出行时间'
      } else if (this.step === 3) {
        return line + '——平均出行距离'
      }
    }
  },
  methods: {
    figureData: function (step) {
      let argument = []
      let amount = []
      let bgColor = []
      let bdColor = []
      if (step === 1) {
        argument = ['南丁格尔玫瑰图', '金字塔图', '条形图', '雷达图', '热力图', '像素图']
        amount = [5, 4, 3, 2, 1, 2]
        bgColor = [
          'rgba(255, 99, 132, 0.2)',
          'rgba(255, 206, 86, 0.2)',
          'rgba(153, 102, 255, 0.2)',
          'rgba(255, 159, 64, 0.2)',
          'rgba(153, 51, 250, 0.2)',
          'rgba(3, 168, 158, 0.2)'
        ]
        bdColor = [
          'rgba(255,99,132,1)',
          'rgba(255, 206, 86, 1)',
          'rgba(153, 102, 255, 1)',
          'rgba(255, 159, 64, 1)',
          'rgba(138, 43, 226, 1)',
          'rgba(0, 199, 140, 1)'
        ]
      } else if (step === 2) {
        argument = ['条形组图', '雷达图', '平滑曲线图']
        amount = [5, 4, 3]
        bgColor = [
          'rgba(255, 159, 64, 0.2)',
          'rgba(153, 51, 250, 0.2)',
          'rgba(3, 168, 158, 0.2)'
        ]
        bdColor = [
          'rgba(255, 159, 64, 1)',
          'rgba(138, 43, 226, 1)',
          'rgba(0, 199, 140, 1)'
        ]
      } else if (step === 3) {
        argument = ['条形图', '雷达图']
        amount = [5, 4]
        bgColor = [
          'rgba(153, 51, 250, 0.2)',
          'rgba(3, 168, 158, 0.2)'
        ]
        bdColor = [
          'rgba(138, 43, 226, 1)',
          'rgba(0, 199, 140, 1)'
        ]
      }
      return {
        labels: argument,
        datasets: [{
          label: 'Star',
          data: amount,
          backgroundColor: bgColor,
          borderColor: bdColor,
          borderWidth: 1
        }]
      }
    }
  },
  mixins: [eagle.slide]
}
</script>
<style lang='scss' scoped>
.eg-slide {
  .eg-slide-content {
    // FIGURE AND CAPTIONS
    .figure {
      p {
        font-size: 0.7em;
        margin-top: 2em;
        margin-bottom: 0;
        color: #555;
      }
      width: 80%;
      margin-left: 10%;
    }
    // SVG ANIMATIONS
    .included-svg {
      width: 80%;
      margin-left: 10%;
      g path {
        transform-origin: center bottom;
        animation-duration: 1s;
        animation-fill-mode: both;
        animation-iteration-count: infinite;
      }
      .svg-bounce path {
        -webkit-animation-name: bounce;
        transform-origin: center bottom;
      }
      .svg-pulse path {
        -webkit-animation-name: pulse;
        -moz-animation-name: bounce;
        transform-origin: center center;
      }
      .svg-swing path {
        -webkit-animation-name: swing;
        -moz-animation-name: bounce;
        transform-origin: center center;
      }
    }

  }
}
</style>
