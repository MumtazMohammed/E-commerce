<template>
  <div>
    <!-- advertisement  -->
    <v-container fluid class="py-0 px-1">
      <v-card
        flat
        rounded="md"
        class="AdvertisementTow"
        height="220"
        style="overflow: hidden"
      >
        <swiper class="swiper" :options="swiperOption">
          <swiper-slide v-for="(item, i) in items" :key="i">
            <v-card
              style="position: absolute"
              width="100%"
              height="100%"
              :color="item.color"
              tile
              flat
              :img="item.src"
              :lazy-src="item.src"
              contain
            >
            </v-card>
            <!-- <v-img contain :src="item.src" :lazy-src="item.src"> </v-img> -->
          </swiper-slide>
          <div class="swiper-pagination" slot="pagination"></div>
        </swiper>
      </v-card>
    </v-container>
  </div>
</template>
<script>
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";

export default {
  name: "AdvertisementTow",
  components: {
    Swiper,
    SwiperSlide,
  },
  setup() {
    return {};
  },
  data() {
    return {
      model: 0,
      items: [
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg",
          color: "#cfbcad",
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/sky.jpg",
          color: "#384c51",
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/bird.jpg",
          color: "#493c32",
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/planet.jpg",
          color: "#1d4552",
        },
      ],
      swiperOption: {
        initialSlide: 0,
        freeMode: false,
        effect: "fade",
        spaceBetween: 10,
        autoplay: {
          delay: 4000,
          disableOnInteraction: true,
          stopOnLastSlide: false,
        },
        loop: false,
        loopFillGroupWithBlank: false,
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
        },
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev",
        },
        breakpoints: {
          1024: {
            slidesPerView: 1,
            slidesPerGroup: 1,
          },
          768: {
            slidesPerView: 1,
            slidesPerGroup: 1,
          },
          640: {
            slidesPerView: 1,
            slidesPerGroup: 1,
          },
          471: {
            slidesPerView: 1,
            slidesPerGroup: 1,
          },
          470: {
            slidesPerView: 1,
            slidesPerGroup: 1,
          },
          250: {
            slidesPerView: 1,
            slidesPerGroup: 1,
          },
        },
      },
    };
  },
};
</script>
<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;800;900&display=swap");
@import "@/scss/virables";
@import "@/scss/mixin";

.swiper {
  height: 220px !important;
  @media (max-width: 600px) {
    height: 180px !important;
  }
  .swiper-pagination::v-deep .swiper-pagination-bullet {
    width: 9px !important;
    border-radius: 50%;
    height: 9px;
    margin: 0 4px;
    background-color: #eee;
  }
  .swiper-pagination::v-deep .swiper-pagination-bullet-active {
    opacity: 1;
  }

  ::v-deep.swiper-container {
    @media (max-width: 600px) {
      padding-right: 5px;
      padding-left: 5px;
    }
  }
}
::v-deep .swiper-container-horizontal > .swiper-pagination-bullets {
  bottom: 0 !important;
}
::v-deep .v-image.v-responsive.theme--light {
  height: 220px !important;
  @media (max-width: 600px) {
    height: 180px !important;
  }
}
.AdvertisementTow {
  @media (max-width: 600px) {
    border-radius: 0px !important;
    height: 180px !important;
  }
}
</style>
