<template>
  <div class="slider__section">
    <div uk-slider="center: true; finite:false; autoplay:true" class="uk-position-relative ">
      <div class="uk-slider-container">
        <ul class="uk-slider-items uk-position-relative">
          <li class="slider__item" v-for="slide in slides">
            <img class="slider__img" src="~/assets/img/slider/slider_1.jpg" width="1920" height="726"
                 alt="">
            <div class="uk-position-center uk-panel">
              <h3 class="slider__subheader" v-html="slide.header">
              </h3>
              <h2 class="slider__header" v-html="slide.subheader" >
              </h2>
              <div class="btn__wrapper uk-flex uk-flex-center">
                <a href="#request" class="request__btn default__btn">
                  {{$t('request_btn')}}
                </a>
              </div>
            </div>
          </li>
        </ul>
        <ul class="uk-slider-nav uk-dotnav"></ul>
      </div>
    </div>
  </div>
</template>
<script setup>
const config = useRuntimeConfig();
const localPath = useLocalePath();
const {locale} = useI18n()
const slides = reactive([
  {
    img_path: `~/assets/img/slider/slider_1.jpg`,
    header: locale === 'en'? 'Request a new project' : 'Запитване на нов проект',
    subheader: locale === 'en'? 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quisquam, quod.' : 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quisquam, quod.'
  },
  {
    img_path: `~/assets/img/slider/slider_2.jpg`,
    header: locale === 'en'? 'Request a new project' : 'Запитване на нов проект',
    subheader: locale === 'en'? 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quisquam, quod.' : 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quisquam, quod.'
  }
])

</script>
<style lang="scss">
.slider__section {
  .uk-slider-nav {
    position: absolute;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);

    li {
      a {
        width: 15px;
        height: 15px;
        border: 1px solid white;
      }

      &.uk-active {
        a {
          background-color: $main-color;
          border: 1px solid $main-color;
        }
      }
    }
  }

  .uk-slider-items {
    .slider__item {
      overflow: hidden;
      max-height: 700px;
      width: 100%;
      color: white;
      min-height: 450px;

      .slider__img {
        height: 100%;
        width: 100%;
        object-fit: cover;
        filter: blur(2px);
      }

      .slider__subheader {
        color: white;
        text-align: center;
        font-size: $fz-16-34;
        font-weight: 300;
        line-height: 1.23em;
        margin-bottom: 20px;

      }

      .slider__header {
        color: white;
        text-align: center;
        margin-top: 0;
        padding: 0 15px;
        font-size: $fz-24-60;
        font-weight: 400;
        text-transform: uppercase;
      }


      @include default-btn();

    }

  }
}

</style>