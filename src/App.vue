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

@import './assets/scss/variables.scss','./assets/scss/mixin.scss', './assets/scss/main.scss';
</style>
