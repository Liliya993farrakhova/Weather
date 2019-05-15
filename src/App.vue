<template>
  <div id="app" class="app" v-bind:class="{ night: darkTheme}">
    <section class="error" v-if="errored">
    <p class="error__paragraph">Сервис погоды временно недоступен.</p>
     <p class="error__paragraph">Попробуйте обратиться позже</p>
  </section>

  <div  v-else class="slider-wrap">
    <slider ref="sliderTiny" v-bind="tinySliderOptions" class="slider"  v-if="listWeathertData">
        <div class="slider__item" v-for="(item,index) in listWeathertData" >
          <div class="background-image__box">
   
            <div v-html="tree" class="background-image background-image__level1"></div>
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
import axios from 'axios';
export default{
  data(){
    return {
        endpoint: "https://gist.githubusercontent.com/anonymous/feb1b31516f3e36a14b29657701f18d2/raw/eaa544aed7e3bdee37c6caa2a515f1d4c38fbd4f/weather.json",
        listWeathertData: null,
        darkTheme: false,
        loading: true,
        errored: false,
        tree : '',
        tinySliderOptions: {
            mouseDrag: true,
            loop: true,
            items: 1,
            autoWidth: false,
            slideBy: 1,
            center: true,
            viewportMax: 400,
            controls: false,
            nav: false,
            
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

        this.tree = require("raw-loader!./assets/images/Man-Reading-Book-Under-Tree-Silhouette.svg")['default'];

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
          .catch(error => {
            console.log(error);
            this.errored = true;
          })
          .finally(() => (this.loading = false));
          

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

@import './assets/scss/variables.scss','./assets/scss/mixin.scss';

  *{
    @include prefix(box-sizing, border-box, webkit ms moz o)
  }
  html,body{
    width: 100%;
    margin: 0;
    padding: 0;
    font-family: 'Khand', sans-serif;
    font-size: $baseFont;
    @media screen and (max-height: $media_Middle_Height) {
      font-size: $media_Middle_Height-baseFont;
    }
  }
  @include keyframes(slide-up) {
    0% { opacity: 0; }
    90% { opacity: 1; }
  }
  .error{
    color: #fff;
    font-size: 2rem;
    &__paragraph{
      text-align: center;
      margin: 0px;
    }
  }
  .app{
    @include flexbox;
    @include prefix(justify-content, center, webkit ms moz o);
    @include prefix(align-items, center, webkit ms moz o);
    min-height: 99.9vh;
    background-color: $blue;
    &.night{
      background-color: $dark_Blue_Body-Color;
      .slider{
        &-wrap{
          background-color: $dark_Blue_App-Color;
        }
        &-thumbnails__preview{
          &.active{
             background-color: $footer_preview_Active_Slide_Dark_Blue-Color;
          }
        }
      }
    }

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
    margin-left: auto;
    margin-right: auto;
    position: absolute;
    bottom: 0px;
    left: 0;
    right: 0;
    &__level1{
      g{
        fill: rgba(365,365,365,0.2);
      }
    }

  }
  .slider{
    margin: 0 auto;
    &__header{
      background-color: rgba(365,365,365,0.1);
      height: $header-Height;
      @include flexbox;
      @include prefix(justify-content, center, webkit ms moz o)
      @include prefix(align-items, center, webkit ms moz o)
      font-size: $header-Font;
      color: #fff;
      position: absolute;
      left: 0;
      right: 0;
      top: 0;
      @media screen and (max-height: $media_Middle_Height) {
        height: $media_Middle_Heightheader-Height;
      }
    }
    &__overcast{
      margin-bottom: $mainWeatherIcon-Margin_to_Elements;
    }
    &-wrap{
     max-width: $app-MaxWidth;
     margin-left: auto;
     margin-right: auto;
     background-color: $light-blue;
     position: relative;
     overflow: hidden;

    }
    &__item{
      padding-top: $header-Height;
      position: relative;
      @media screen and (max-height: $media_Middle_Height) {
        padding-top: $media_Middle_Heightheader-Height;
      }
    }
    &__icon{
      width: $mainWeatherIcon-Square;
      height: $mainWeatherIcon-Square;
      margin-left: auto;
      margin-right: auto;
      fill: #fff;
      &-wrap{
        width: $mainWeatherIcon_MainHalo-Square;
        height: $mainWeatherIcon_MainHalo-Square;
        margin: 0 auto;
        background-color: rgba(365,365,365,0.2);
        @include flexbox;
        @include prefix(align-items, center, webkit ms moz o)
        @include prefix(border-radius, 50%, webkit ms moz o)
        position: relative;
        @media screen and (max-height: $media_Middle_Height) {
          width: $media_Midlle_Height_mainWeatherIcon_MainHalo-Square;
          height: $media_Midlle_Height_mainWeatherIcon_MainHalo-Square;
        }
        &::before{
          content: "";
          display: block;
          position: absolute;
          width: $mainWeather_IconHalo-Square;
          height: $mainWeather_IconHalo-Square;
          top: 50%;
          margin-top: -($mainWeather_IconHalo-Square/2);
          left: 50%;
          margin-left: -($mainWeather_IconHalo-Square/2);
          background-color: rgba(365,365,365,0.2);
          z-index: 0;
          @include prefix(border-radius, 50%, webkit ms moz o);
          @media screen and (max-height: $media_Middle_Height) {
            width: $media_Midlle_Height_mainWeather_IconHalo-Square;
            height: $media_Midlle_Height_mainWeather_IconHalo-Square;
             margin-left: -($media_Midlle_Height_mainWeather_IconHalo-Square/2);
             margin-top: -($media_Midlle_Height_mainWeather_IconHalo-Square/2);
          }
        }
      }
    }
    &__content{
      position: relative;
      min-height: $appContent-MinHeight;
      padding: $appContent-Padding;
      flex-wrap: wrap;
      font-size: $appContent-FontSize;
      color: #fff;
      &_text-center{
        text-align: center;
      }
      @media screen and (max-height: $media_Middle_Height) {
        min-height: $media_Middle_AppContent-MinHeight;
      }
      @media screen and (max-height: $media_Small_Height) {
        min-height: 0;
        height: $media_SmallHeight_AppContent-MinHeight;
      }
    }
    &__footer{
      margin-top: $mainWeatherIcon-Margin_to_Elements;
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
        padding: $footer_preview-padding;
        cursor: pointer;
        @include prefix(justify-content, center, webkit ms moz o);
        text-align: center;
        &.active{
          background-color: $footer_preview_Active_Slide_Blue-Color;
          @include animation('slide-up 0.2s linear 1');
        }
      }
      &__svg{
        fill: #fff;
        width: $footer_preview-Square;
        height: $footer_preview-Square;

      }
      &__time{
        width: 100%;
      }
    }
  }
  
</style>
