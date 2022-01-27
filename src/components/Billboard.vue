<template>
  <div
    :style="`background-color: ${currentColor};`"
    class="billboard">
    <div class="inner">
      <div
        ref="swiper"
        class="swiper">
        <div class="swiper-wrapper">
          <div
            v-for="item in billboards"
            :key="item.name"
            class="swiper-slide">
            <img
              :data-src="item.src"
              class="swiper-lazy" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import Swiper from 'swiper/bundle'
import 'swiper/css/bundle'

export default {
  data() {
    return {
      billboards: [],
      swiper: null
    }
  },
  mounted() {
    this.init()
  },
  methods: {
    async init () {
      this.rankings = await this.$fetch({
        requestName: 'rankings'
      })
      console.log(this.rankings)
    }
  }
}
</script>

<style scoped lang="scss">
  .billboard {
    transition: background-color 1s;
  }
  .swiper {
    width: 1240px;
    height: 400px;
    .swiper-lazy-preloader {
      border-color: #F43242;
      border-top-color: transparent;
    }
  }
  .controls {
    display: flex;
    position: absolute;
    bottom: 25px;
    right: 0;
    z-index: 1;
    .controller {
      background-color: rgba(#000, .2);
      border-radius: 22.5px;
      margin-right: 10px;
      display: flex;
      &:last-child {
        margin-right: 0;
      }
      .autoplay {
        width: 45px;
        height: 45px;
        cursor: pointer;
        display: flex;
        justify-content: center;
        align-items: center;
        &.pause {
          &::after {
            background-position: -170px -29px;
          }
        }
        &::after {
          content: "";
          display: block;
          width: 24px;
          height: 24px;
          background-image: url("https://trusting-williams-8cacfb.netlify.app/images/main_2x.png");
          background-position: -170px -87px;
          background-size: 209px;
        }
      }
    }
  }
</style>
