<template>
  <div>
    <!--Main Slider Part Start-->
    <div class="main_slider">
      <div class="main_slider_bg_part">
        <h2 style="text-align: center; text-transform: uppercase; color: #fff; margin-bottom: 10px;" class="h2Responsive ">
          {{ this.$parent.contentData.second_title }}
        </h2>
        <div class="container-lg"   v-show="isPlaceholder" >
          <vue-content-loading :width="300" :height="115"  >
            <img @load="onImageLoad" hidden>
            <rect  x="0" y="0" rx="2" ry="2" width="300" height="105" />
          </vue-content-loading>
        </div>


        <div class="container-lg" v-show="isImageLoaded">
          <div class="slider">
            <div class="item">
              <picture>
                <!--                <source :srcset="this.$parent.contentData.static_image" media="(max-width: 600px)">-->
                <!--                <source :srcset="this.$parent.contentData.static_image">-->
                <img :src="this.$parent.contentData.static_image" alt="Slider Image" @load="onImageLoad">
              </picture>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!--Main Slider Part End-->
  </div>
</template>

<script>
  import VueContentLoading from 'vue-content-loading';
  export default {
    components: {
          VueContentLoading,
      AppFooter: () => import('../../incudes/Footer'),
    },
    data() {
      return {
        contentData: '',
        isImageLoaded: false,
        isPlaceholder: true,
      }
    },
    methods: {
      onImageLoad () {
        this.isPlaceholder = false;
        this.isImageLoaded = true;
        // this.$store.state.isLoading =false;
      },

    }


  };



</script>

<style lang="" scoped>
  .owl-dots {
    text-align: center;
    -webkit-tap-highlight-color: transparent;
    position: absolute !important;
    bottom: 100px;
    bottom: 80px;
    left: 105px;
  }
</style>
