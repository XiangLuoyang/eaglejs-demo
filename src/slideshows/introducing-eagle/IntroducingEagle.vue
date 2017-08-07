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
      h3 如何描述

      .center
        eg-transition(enter='bounceInLeft' leave='bounceOutLeft')
          p(v-if="step >= 2")
            | 基于
            img(src='./assets/icons/shijian.svg' width='40px' height='40px')
            | |
            img(src='./assets/icons/kongjian.svg' width='50px' height='50px')
            | |
            img(src='./assets/icons/gongneng.svg' width='50px' height='50px')
            | 三个维度对数据进行描述
        eg-transition(enter='bounceInRight' leave='bounceOutLeft')
          p(v-if="step >= 3")
            | 依据 关联、比重、次数、趋势、轨迹等关键词进行描述
        eg-transition(enter='bounceInLeft' leave='bounceOutRight')
          p(v-if="step >= 4")
            | 过程 = (正确的描述) => 合理的制图

    //- slide(:steps=1, leave='fadeOut')
    //-   eg-transition(enter='flipInX')
    //-     h3 接上面，这张讲基于时间维度的画图方式，有那些图要做。

    //-   eg-transition(enter='flipInX')
    //-     p 分成两张ppt写出关键词为时间的图可以有哪些选项，什么情况下用什么图

    //-   eg-transition(enter='flipInX')
    //-     eg-code-block(lang='html').
    //-       1. 在基于时间的情况下什么情况下用什么图

    //- slide(:steps=1, leave='fadeOut')
    //-   eg-transition(enter='flipInX')
    //-     h3 接上面，这张讲基于空间维度的画图方式，有那些图要做。

    //-   eg-transition(enter='flipInX')
    //-     p 分成两张ppt写出关键词为空间的图可以有哪些选项，什么情况下用什么图

    //-   eg-transition(enter='flipInX')
    //-     eg-code-block(lang='html').
    //-       1. 在基于空间的情况下什么情况下用什么图

    //- slide.boredYet(enter='fadeIn', :mouseNavigation='false', :keyboardNavigation='false')
    //-   h3 Bored yet ?
    //-   .center
    //-     p What shall I call you ?
    //-     input.center(v-model='username')
    //-     p.
    //-       {{ username }}<span v-if='username.length'>,</span> I got you.
    //-       Tell me what you like, I'll skip the rest:

    //-     .inline(v-for='category, name in slideCategories')
    //-         eg-toggle(:key='name', v-model='category.show', :width='30',
    //-                   on-text='', off-text='', on-color='#ffeeaa',
    //-                   @change='changeMessage(category.changeMessage)')
    //-           p.label {{ category.name }}
    //-           eg-triggered-message(:trigger='!category.show',
    //-                               :duration='3', position='top right',
    //-                               enter='bounceInRight', leave='bounceOutRight')
    //-             p(v-html="message(category.name)")

    //-   .center
    //-     p What's your favourite ?
    //-     eg-radio.inline(v-for='pref in preferences', v-model="preference",
    //-                     :label="pref.label" )
    //-       p {{ pref.text}}
    //-       eg-triggered-message(:trigger='preference=== pref.label',
    //-                           :duration='3', position='top right',
    //-                           enter='bounceInRight', leave='bounceOutRight')
    //-                       p {{ message(pref.label) }}

    //-   .button.prev(@click.stop='previousSlide')
    //-     span &lt; Prev. slide
    //-     br
    //-     span.small  Ctrl + left
    //-   .button.next(@click.stop='nextSlide')
    //-     span Next slide &gt;
    //-     br
    //-     span.small Ctrl + right



    //- themes-slideshow(:skip="!slideCategories.themes.show", :inserted='true', firstSlide=3)
    vtfpourt3x(enter='flipInY', leave='flipOutY')
    vtfpourt4x(enter='bounceInRight', leave='bounceOutRight')
    vtfpourt5x(enter='flipInX', leave='flipOutX')
    vtfpourt6x(enter='bounceInLeft', leave='bounceOutLeft')
    //- awesome-inserted-slide(:username='username', :preference='preference',
    //-                        enter='fadeIn', leave='hinge',
    //-                        :skip="!slideCategories['slideReuse'].show")

    //- figures-slide(enter='flipInY', leave='rollOut', :skip="['slideReuse', 'themes', 'interactivity'].some(function (e) {return slideCategories[e].show})")

    //- 插入图表的ppt
    figures-slide(:inserted='true')

    slide(enter='zoomIn', leave='fadeOut')
      h3 That's all folks !
      p.center Think you can help ?
      .center
        img.computerkid.shadowbox(src='http://i.imgur.com/AAlntwU.gif')
      p.center.
        I'm not a frontend person, so everyone<br />
        is welcome to contribute to <a href="https://github.com/Zulko/eagle.js" target='_blank'> the repo</a>.


    slide(enter='fadeIn')
      h3 Thank you !
      p This slideshow's so fresh, it has end credits.
      end-credits(:username='username')
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
