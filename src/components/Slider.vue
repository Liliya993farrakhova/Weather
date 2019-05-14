<template>
	<div class="wrap slider slider_blue">
		<tiny-slider ref="sliderTiny" v-bind="tinySliderOptions" class="slider__visible-part">
			<div class="slider__item">
				<header class="slider__header">
					<span class="slider__time">
						time
					</span>
				</header>
				<div class="slider__content">
					<div class="slider__overcast">
						overcast
					</div>
					<div class="slider__icon-wrap">
						<div class="slider__icon">
							icon
						</div>
					</div>
					<div class="slider__temperature">
						temperature
					</div>
				</div>
			</div>
			<div class="slider__item">
				<header class="slider__header">
					<span class="slider__time">
						time
					</span>
				</header>
				<div class="slider__content slider__content_blue">
					<div class="slider__overcast">
						overcast
					</div>
					<div class="slider__icon-wrap">
						<div class="slider__icon">
							icon
						</div>
					</div>
					<div class="slider__temperature">
						temperature
					</div>
				</div>
			</div>
			<div class="slider__item">
				<header class="slider__header">
					<span class="slider__time">
						time
					</span>
				</header>
				<div class="slider__content slider__content_blue">
					<div class="slider__overcast">
						overcast
					</div>
					<div class="slider__icon-wrap">
						<div class="slider__icon">
							icon
						</div>
					</div>
					<div class="slider__temperature">
						temperature
					</div>
				</div>
			</div>
		</tiny-slider>
	</div>
	
</template>
<script>
	import vueTinySlider from 'vue-tiny-slider';

	export default{
        data(){
            return {
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
				    nav: true
				}
            }
        },
        components: {
            "tiny-slider": vueTinySlider
        },
        updated(){

			let slider = refs.sliderTiny.slider;
			let thumbnail = document.getElementsByClassName('slider-user__thumbnail');

			Array.prototype.forEach.call(thumbnail, function(el) {

				el.onclick = function(){

					for (var i = 0; i < thumbnail.length; i++) {

						if (el == thumbnail[i]) {

							slider.goTo(i);

						}

					}

				}

			});
        }
    }


</script>
<style lang="scss">
	.slider{
		max-width: 400px;
		margin: 0 auto;
		&_blue{
			min-height: 250px;
			background-color: #22a5da;
		}
		&__item{
			
		}
		&__visible-part{
			max-width: 400px;
			margin: 0 auto;
		}
		&__content{

		}
	}
</style>