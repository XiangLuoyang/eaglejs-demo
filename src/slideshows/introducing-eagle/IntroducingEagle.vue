<template lang="pug">
#IntroducingEagle.eg-theme-agrume
  .eg-slideshow
    slide(enter='fadeIn' leave='bounceOutLeft')
      .center.frontpage
        h1 VISUALIZATION TECHNOLOGY
        img(src='./assets/fm.png')
        h4 FOR PASENGERS OF URBAN RAIL TRANSIT
        eg-triggered-message(:trigger='slideTimer >= 2',
                            :duration='6', position='top right',
                            enter='bounceInRight', leave='bounceOutRight')
          p Next:
          img.control-schema(src='./assets/controlsNext.svg')
          p Previous:
          img.control-schema(src='./assets/controlsPrev.svg')
    slide(:steps=5, enter='bounceInRight' leave='bounceOutDown')
      h3
        | 提纲
        .inline(class='animated infinite pulse heart')
        | Outlines
      eg-transition(enter='fadeIn' leave='fadeOut')
        .quarter(v-if='step >=2')
          img(src='./assets/icons/tongji.svg')
          h4 客流统计
          p Passenger flow estimation

      eg-transition(enter='fadeIn' leave='fadeOut')
        .quarter(v-if='step >=3')
          img(src='./assets/icons/guiji.svg')
          h4 移动轨迹
          p Moving trajectory

      eg-transition(enter='fadeIn' leave='fadeOut')
        .quarter(v-if="step >= 4")
         img(src='./assets/icons/tezheng.svg')
         h4 出行特征
         p Trip characteristics

      eg-transition(enter='fadeIn' leave='fadeOut')
        .quarter(v-if="step >= 5")
          img(src='./assets/icons/leibie.svg')
          h4 类别
          p Category

      eg-transition(enter='fadeIn' leave='fadeOut')
        eg-modal(v-if='step >= 6')
          h3 You right now:
          .center
            img(:src="preloadedImages['youRightNow']",
                :style="{height: '10em'}")


    slide(:steps=4, enter='bounceInDown')
      h3.center 如何描述
      br
      .center
        eg-transition(enter='bounceInLeft' leave='bounceOutLeft')
          p.center(v-if="step >= 2")
            | 基于
            img(src='./assets/icons/shijian.svg' width='40px' height='40px')
            | |
            img(src='./assets/icons/kongjian.svg' width='50px' height='50px')
            | |
            img(src='./assets/icons/gongneng.svg' width='50px' height='50px')
            | 三个维度对数据进行描述
        br
        eg-transition(enter='bounceInRight' leave='bounceOutLeft')
          p.center(v-if="step >= 3")
            | 依据 关联、比重、次数、趋势、轨迹等关键词进行描述
        br
        eg-transition(enter='bounceInLeft' leave='bounceOutRight')
          p.center(v-if="step >= 4")
            | 过程 = (正确的描述) => 合理的制图

    vtfpourt3x(enter='flipInY', leave='flipOutY')
    vtfpourt4x(enter='bounceInRight', leave='bounceOutRight')
    vtfpourt5x(enter='flipInX', leave='flipOutX')
    vtfpourt6x(enter='bounceInLeft', leave='bounceOutLeft')

    slide(enter='zoomIn', leave='fadeOut')
      h3 That's all!
      p.center Think you can help ?
      .center
        img.computerkid.shadowbox(src='http://i.imgur.com/AAlntwU.gif')
      p.center.
        chaosx@yeah.net

    slide(enter='fadeIn')
      h3 Thank you !
</template>

<script>
import eagle from 'eagle.js'

export default {
  mixins: [eagle.slideshow],
  infos: {
    title: '可视化技术',
    description: '城市轨道交通客流出行',
    path: 'introducing-eagle'
  },
  components: {
    'vtfpourt3x': require('./Vtfpourt3x'),
    'vtfpourt4x': require('./Vtfpourt4x'),
    'vtfpourt5x': require('./Vtfpourt5x'),
    'vtfpourt6x': require('./Vtfpourt6x'),
    'awesome-inserted-slide': require('./AwesomeInsertedSlide'),
    'figures-slide': require('./FiguresSlide'),
    'end-credits': require('./components/EndCredits'),
    'themes-slideshow': require('../themes-slideshow/ThemesSlideshow')
  },
  data: function () {
    return {
      username: 'Tracy',
      preference: 'baby bunnies',
      preferences: [
        {
          label: 'baby bunnies',
          text: 'Baby bunnies'
        },
        {
          label: 'fluffy puppies',
          text: 'Fluffy puppies'
        },
        {
          label: 'funny kitties',
          text: 'Funny kitties'
        }
      ],
      slideCategories: {
        themes: {
          show: true,
          name: 'Theming'
        },
        slideReuse: {
          show: true,
          name: 'Slide reuse'
        },
        interactivity: {
          show: true,
          name: 'Interactivity'
        }
      },
      preloadedImages: {
        computerKid: 'http://i.imgur.com/AAlntwU.gif',
        youRightNow: 'http://i.imgur.com/DFBTj0a.gif',
        bretagne: 'http://i.imgur.com/rYkJ6I8.jpg',
        forrestRoad: 'http://i.imgur.com/hxTMFZW.jpg',
        starrySky: 'http://i.imgur.com/yO2ivoD.jpg',
        cityBokeh: 'http://i.imgur.com/kmmHith.jpg',
        darkWoods: 'http://i.imgur.com/FL9mwpd.jpg'
      }
    }
  },
  methods: {
    message: function (name) {
      return {
        'baby bunnies': 'Yeeeeah my favorite too !',
        'fluffy puppies': 'Wow so original.',
        'funny kitties': 'Good for you ' + this.username + '.',
        'Theming': 'Ok ' + this.username + ', whatever.',
        'Slide reuse': 'Seriously ' + this.username + ' you <em>want</em> to see this.',
        'Interactivity': 'Well that\'s this slide, ' + this.username +
                         '. <br /> A bit too late to unsee it, heh ?'
      }[name]
    }
  }
}
</script>

<style lang='scss'>
@import 'node_modules/eagle.js/src/themes/agrume/agrume';
#IntroducingEagle {
  h3 {
    font-family: '微软雅黑';
  }
  h4 {
    font-family: 'Pompiere','微软雅黑';
  }
  p {
    font-family: 'Pompiere','微软雅黑';
  }
  .frontpage {
    img {
      height: 7em;
    }
    img.control-schema {
      width: 8em;
      height: 3em;
    }
  }
  .heart {
    width: 1em;
    height: 0.8em;
    margin-left: 0.1em;
    margin-right: 0.1em;
    background-image: url('./assets/heart.svg');
    background-position: center center;
    background-repeat:  no-repeat;
    background-size: contain;

  }

  .quarter {
    text-align: center;
    p {
      margin-top: 0;
      text-align: center;
    }
    h4 {
      margin-top: 0;
      margin-bottom: 0
    }
  }
  .boredYet {
    p {
      margin-bottom: 0.3em;
      margin-top: 1.3em;
    }
    .button {
      border: none;
    }
    .button.prev {
      float: left;
    }
    .button.next {
      float: right;
    }
  }
  img.computerkid {
    height: 6.5em;
  }

  a {
    color: black;
  }
}
</style>
