<template>
  <div id="app" class="app">
  <div class="slider-wrap">
    <slider ref="sliderTiny" v-bind="tinySliderOptions" class="slider"  v-if="listWeathertData">
        <div class="slider__item" v-for="(item,index) in listWeathertData" >
          <div class="background-image__box">
            <svg class="background-image background-image__level1 " version="1.0" viewBox="0 0 1280.000000 820.000000"
            preserveAspectRatio="xMidYMid meet">
            <g transform="translate(0.000000,820.000000) scale(0.100000,-0.100000)" stroke="none">
            <path d="M11815 8182 c-58 -27 -103 -76 -253 -269 -73 -94 -178 -220 -234
            -280 -55 -59 -146 -169 -201 -243 -55 -74 -160 -196 -232 -270 -72 -74 -161
            -174 -198 -221 -37 -47 -104 -117 -149 -155 -150 -127 -217 -190 -248 -232
            -16 -23 -34 -42 -39 -42 -5 0 -39 -40 -76 -90 -63 -85 -69 -90 -104 -90 -80 0
            -187 -26 -437 -106 l-141 -46 -49 25 c-72 36 -155 51 -254 43 -47 -3 -150 -10
            -230 -16 -133 -9 -197 -21 -350 -63 -71 -20 -297 -57 -345 -57 -25 0 -47 8
            -68 26 -16 14 -56 38 -87 54 -32 16 -109 62 -171 103 -63 41 -141 87 -173 102
            -32 15 -102 60 -155 100 -131 98 -231 151 -311 164 -37 7 -107 31 -162 57
            -105 50 -171 63 -323 64 -89 0 -252 -35 -332 -71 -71 -33 -234 -202 -318 -330
            -38 -57 -108 -145 -155 -195 -48 -50 -121 -135 -162 -191 -91 -119 -150 -173
            -234 -213 -79 -38 -132 -39 -199 -4 -251 134 -492 318 -790 603 -61 58 -167
            150 -237 204 -242 187 -357 333 -519 658 -99 198 -199 348 -313 468 -203 214
            -264 253 -434 277 -59 9 -132 25 -162 36 -206 75 -189 71 -260 59 -91 -15
            -198 -71 -276 -143 -35 -33 -128 -140 -206 -237 -229 -283 -435 -477 -634
            -596 -93 -56 -131 -86 -188 -148 -211 -233 -252 -269 -428 -380 -111 -69 -155
            -82 -264 -73 -125 9 -193 46 -364 195 -136 119 -202 185 -264 266 -33 43 -66
            86 -73 95 -10 12 -12 -736 -13 -3502 l0 -3518 6400 0 6400 0 0 3879 0 3879
            -52 39 c-29 22 -80 57 -113 79 -33 22 -116 78 -185 125 -98 67 -154 97 -258
            138 -122 48 -141 53 -235 57 -86 4 -108 2 -142 -14z"/>
            </g>
            </svg>
            <svg class="background-image background-image__level2 " version="1.0" viewBox="0 0 1280.000000 820.000000"
            preserveAspectRatio="xMidYMid meet">
            <g transform="translate(0.000000,820.000000) scale(0.100000,-0.100000)" stroke="none">
            <path d="M11815 8182 c-58 -27 -103 -76 -253 -269 -73 -94 -178 -220 -234
            -280 -55 -59 -146 -169 -201 -243 -55 -74 -160 -196 -232 -270 -72 -74 -161
            -174 -198 -221 -37 -47 -104 -117 -149 -155 -150 -127 -217 -190 -248 -232
            -16 -23 -34 -42 -39 -42 -5 0 -39 -40 -76 -90 -63 -85 -69 -90 -104 -90 -80 0
            -187 -26 -437 -106 l-141 -46 -49 25 c-72 36 -155 51 -254 43 -47 -3 -150 -10
            -230 -16 -133 -9 -197 -21 -350 -63 -71 -20 -297 -57 -345 -57 -25 0 -47 8
            -68 26 -16 14 -56 38 -87 54 -32 16 -109 62 -171 103 -63 41 -141 87 -173 102
            -32 15 -102 60 -155 100 -131 98 -231 151 -311 164 -37 7 -107 31 -162 57
            -105 50 -171 63 -323 64 -89 0 -252 -35 -332 -71 -71 -33 -234 -202 -318 -330
            -38 -57 -108 -145 -155 -195 -48 -50 -121 -135 -162 -191 -91 -119 -150 -173
            -234 -213 -79 -38 -132 -39 -199 -4 -251 134 -492 318 -790 603 -61 58 -167
            150 -237 204 -242 187 -357 333 -519 658 -99 198 -199 348 -313 468 -203 214
            -264 253 -434 277 -59 9 -132 25 -162 36 -206 75 -189 71 -260 59 -91 -15
            -198 -71 -276 -143 -35 -33 -128 -140 -206 -237 -229 -283 -435 -477 -634
            -596 -93 -56 -131 -86 -188 -148 -211 -233 -252 -269 -428 -380 -111 -69 -155
            -82 -264 -73 -125 9 -193 46 -364 195 -136 119 -202 185 -264 266 -33 43 -66
            86 -73 95 -10 12 -12 -736 -13 -3502 l0 -3518 6400 0 6400 0 0 3879 0 3879
            -52 39 c-29 22 -80 57 -113 79 -33 22 -116 78 -185 125 -98 67 -154 97 -258
            138 -122 48 -141 53 -235 57 -86 4 -108 2 -142 -14z"/>
            </g>
            </svg>
            <svg class="background-image background-image__level3 " version="1.0" viewBox="0 0 1280.000000 820.000000"
            preserveAspectRatio="xMidYMid meet">
            <g transform="translate(0.000000,820.000000) scale(0.100000,-0.100000)" stroke="none">
            <path d="M11815 8182 c-58 -27 -103 -76 -253 -269 -73 -94 -178 -220 -234
            -280 -55 -59 -146 -169 -201 -243 -55 -74 -160 -196 -232 -270 -72 -74 -161
            -174 -198 -221 -37 -47 -104 -117 -149 -155 -150 -127 -217 -190 -248 -232
            -16 -23 -34 -42 -39 -42 -5 0 -39 -40 -76 -90 -63 -85 -69 -90 -104 -90 -80 0
            -187 -26 -437 -106 l-141 -46 -49 25 c-72 36 -155 51 -254 43 -47 -3 -150 -10
            -230 -16 -133 -9 -197 -21 -350 -63 -71 -20 -297 -57 -345 -57 -25 0 -47 8
            -68 26 -16 14 -56 38 -87 54 -32 16 -109 62 -171 103 -63 41 -141 87 -173 102
            -32 15 -102 60 -155 100 -131 98 -231 151 -311 164 -37 7 -107 31 -162 57
            -105 50 -171 63 -323 64 -89 0 -252 -35 -332 -71 -71 -33 -234 -202 -318 -330
            -38 -57 -108 -145 -155 -195 -48 -50 -121 -135 -162 -191 -91 -119 -150 -173
            -234 -213 -79 -38 -132 -39 -199 -4 -251 134 -492 318 -790 603 -61 58 -167
            150 -237 204 -242 187 -357 333 -519 658 -99 198 -199 348 -313 468 -203 214
            -264 253 -434 277 -59 9 -132 25 -162 36 -206 75 -189 71 -260 59 -91 -15
            -198 -71 -276 -143 -35 -33 -128 -140 -206 -237 -229 -283 -435 -477 -634
            -596 -93 -56 -131 -86 -188 -148 -211 -233 -252 -269 -428 -380 -111 -69 -155
            -82 -264 -73 -125 9 -193 46 -364 195 -136 119 -202 185 -264 266 -33 43 -66
            86 -73 95 -10 12 -12 -736 -13 -3502 l0 -3518 6400 0 6400 0 0 3879 0 3879
            -52 39 c-29 22 -80 57 -113 79 -33 22 -116 78 -185 125 -98 67 -154 97 -258
            138 -122 48 -141 53 -235 57 -86 4 -108 2 -142 -14z"/>
            </g>
            </svg>
          </div>
          <header class="slider__header">
            {{item.time}}
          </header>
          <div class="slider__content slider__content_text-center flex-wrap">
            <div class="slider__overcast flex-wrap__item flex-wrap__item_full-width">
              {{item.overcast}}
            </div>
            <div class="slider__icon-wrap flex-wrap__item flex-wrap__item_full-width">
              <div v-html="item.iconSvg" class="slider__icon"></div>
            </div>
            <footer class="slider__footer flex-wrap__item  flex-wrap__item_full-width">
              {{item.temperature}}
            </footer>
          </div>
          
        </div>       
    </slider>
      <div class="slider-thumbnails" v-if="listWeathertData">
        <div v-for="(item,index) in listWeathertData"  v-bind:class="{ active: active[index].isActive}" class="slider-thumbnails__preview">
          <div v-html="item.iconSvg" class="slider-thumbnails__svg"></div>
            <div class="slider-thumbnails__time">
            {{item.time}}    
            </div>
        </div>
      </div>
  </div>
  </div>
</template>

<script>
import vueTinySlider from 'vue-tiny-slider';
import axios from 'axios'
export default{
  data(){
    return {
        endpoint: "https://gist.githubusercontent.com/anonymous/feb1b31516f3e36a14b29657701f18d2/raw/eaa544aed7e3bdee37c6caa2a515f1d4c38fbd4f/weather.json",
        listWeathertData: null,
        tinySliderOptions: {
            mouseDrag: true,
            loop: true,
            items: 1,
            autoWidth: false,
            slideBy: 1,
            center: true,
            viewportMax: 400,
            controls: false,
            nav: false
        },
        active:{
          0:{
            isActive: true
          },
          1:{
            isActive: false
          },
          2:{
            isActive: false
          }
        }
    }
  },
  components: {
      "slider": vueTinySlider
  },
  methods:{
      getData(){
          axios.get(this.endpoint).then(response => {
              this.listWeathertData = response.data.list;
              for (var i = 0; i < this.listWeathertData.length; i++) {
                  this.listWeathertData[i]['time'] = this.getTime(this.listWeathertData[i].dt);
                  this.listWeathertData[i]['overcast'] = this.listWeathertData[i].weather[0].description;
                  this.listWeathertData[i]['overcast'] = this.listWeathertData[i].weather[0].description;
                  this.listWeathertData[i]['temperature'] = this.convertTemperature((this.listWeathertData[i].temp.max + this.listWeathertData[i].temp.min)/2);
                   this.listWeathertData[i]["iconSvg"] = require("raw-loader!./assets/images/" + this.listWeathertData[i].weather[0].icon + ".svg")['default'];
              }
              console.log(this.listWeathertData);
          })
          .catch(error => console.log(error));;
      },
      convertTemperature(temp) {
          return Math.round( +(temp) - 273.15) + '°C';
      },
      getTime(timeData){

          var unixtimestamp = timeData;

          var months_arr = ['January','February','March','April','May','June','July','August','September','October','November','December'];

          var date = new Date(unixtimestamp*1000);

          var year = date.getFullYear();

          var month = months_arr[date.getMonth()];

          var day = date.getDate();

          var hours = date.getHours();

          var minutes = "0" + date.getMinutes();

          var seconds = "0" + date.getSeconds();

          var convdataTime = month + ' ' + day + ', ' + year;

           return convdataTime;
      }
  },
  beforeMount(){
      this.getData();
      

  },
  updated(){

    var refs = this.$refs;

    console.log(refs.sliderTiny);

    let slider = refs.sliderTiny.slider;
    
    let thumbnail = document.getElementsByClassName('slider-thumbnails__preview');

    let activeFlag = this.active;
    
    Array.prototype.forEach.call(thumbnail, function(el) {

        el.onclick = function(){


            for (var i = 0; i < thumbnail.length; i++) {

                activeFlag[i].isActive = false;
                
                if (el == thumbnail[i]) {

                    activeFlag[i].isActive = true;

                    slider.goTo(i);
                }
            }
        }
        
    });
  }
}
</script>

<style lang="scss">

  @mixin prefix($property, $value, $prefixes: ()) {
    @each $prefix in $prefixes {
      #{'-' + $prefix + '-' + $property}: $value;
    }
    #{$property}: $value;
  }

  @mixin flexbox() {
    display: -webkit-box;
    display: -moz-box;
    display: -ms-flexbox;
    display: -webkit-flex;
    display: flex;
  }

  *{
    @include prefix(box-sizing, border-box, webkit ms moz o)
  }
  html,body{
    width: 100%;
    margin: 0;
    padding: 0;
    font-family: 'Khand', sans-serif;
    font-size: 18px;
    background-color: #06B0FB;
    @media screen and (max-height: 560px) {
      font-size: 16px;
    }
  }
  .app{
    @include flexbox;
    @include prefix(justify-content, center, webkit ms moz o);
    @include prefix(align-items, center, webkit ms moz o);
    min-height: 99.9vh;
  }
  .flex-wrap{
    &__item{
      &_full-width{
        width: 100%;
      }
    }
  }
  .background-image{
    &__box{
      position: absolute;
      left: 0;
      bottom: 0;
      right: 0;
      z-index: 0;
    }
    width: 100%;
    fill: rgba(0,0,0,0.2);
    position: absolute;
    bottom: 0px;
    left: 0;
    right: 0;
    &__level1{
      z-index: 0;
      fill: rgba(0,0,0,0.5);
      bottom: -10px;
    }
    &__level2{
      z-index: 1;
      left: -64px;

    }
    &__level3{
      z-index: 2;
      left: -168px;
    }

  }
  .slider{
    margin: 0 auto;
    &__header{
      background-color: rgba(365,365,365,0.1);
      height: 60px;
      @include flexbox;
      @include prefix(justify-content, center, webkit ms moz o)
      @include prefix(align-items, center, webkit ms moz o)
      font-size: 1.5rem;
      color: #fff;
      position: absolute;
      left: 0;
      right: 0;
      top: 0;
      @media screen and (max-height: 560px) {
        height: 40px;
      }
    }
    &__overcast{
      margin-bottom: 40px;
    }
    &-wrap{
     max-width: 400px;
     margin-left: auto;
     margin-right: auto;
     background-color: #19B4FB;
     position: relative;
     overflow: hidden;

    }
    &__item{
      padding-top: 60px;
      position: relative;
      @media screen and (max-height: 560px) {
        padding-top: 40px;
      }
    }
    &__icon{
      width: 70px;
      height: 70px;
      margin-left: auto;
      margin-right: auto;
      fill: #fff;
      &-wrap{
        width: 100px;
        height: 100px;
        margin: 0 auto;
        background-color: rgba(365,365,365,0.2);
        @include flexbox;
        @include prefix(align-items, center, webkit ms moz o)
        @include prefix(border-radius, 50%, webkit ms moz o)
        position: relative;
        @media screen and (max-height: 560px) {
          width: 80px;
          height: 80px;
        }
        &::before{
          content: "";
          display: block;
          position: absolute;
          width: 160px;
          height: 160px;
          top: 50%;
          margin-top: -80px;
          left: 50%;
          margin-left: -80px;
          background-color: rgba(365,365,365,0.2);
          z-index: 0;
          @include prefix(border-radius, 50%, webkit ms moz o);
          @media screen and (max-height: 560px) {
            width: 120px;
            height: 120px;
             margin-left: -60px;
             margin-top: -60px;
          }
        }
      }
    }
    &__content{
      position: relative;
      min-height: 500px;
      padding: 30px 0;
      flex-wrap: wrap;
      font-size: 1.4rem;
      color: #fff;
      &_text-center{
        text-align: center;
      }
      @media screen and (max-height: 560px) {
        min-height: 0;
        height: 420px;
      }
      @media screen and (max-height: 480px) {
        min-height: 0;
        height: 360px;
      }
    }
    &__footer{
      margin-top: 40px;
    }
    &-thumbnails{
      @include flexbox;
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      background-color: rgba(25,180,251,0.1);
      color: #fff;
      &__preview{
        @include flexbox;
        @include prefix(flex-grow, 1, webkit ms moz o);
        @include prefix(flex-wrap, wrap, webkit ms moz o);
        @include prefix(align-items, center, webkit ms moz o);
        padding: 10px 0;
        cursor: pointer;
        @include prefix(justify-content, center, webkit ms moz o);
        text-align: center;
        &.active{
          background-color: rgba(25,180,251,1);
        }
      }
      &__svg{
        fill: #fff;
        width: 50px;
        height: 50px;

      }
      &__time{
        width: 100%;
      }
    }
  }
  
</style>
