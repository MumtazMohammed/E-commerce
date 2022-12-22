<template>
  <div>
    <!-- advertisement  -->
    <v-container fluid class="pa-0">
      <swiper class="swiper" :options="swiperOption">
        <swiper-slide v-for="(item, i) in items" :key="i">
          <v-card
            style="position: absolute"
            width="100%"
            height="100%"
            :color="item.color"
            tile
            flat
          >
          </v-card>
          <v-img contain :src="item.src" :lazy-src="item.src"> </v-img>
        </swiper-slide>
        <div class="swiper-pagination" slot="pagination"></div>
      </swiper>
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
  height: 330px !important;
  @media (max-width: 600px) {
    height: 180px !important;
  }

  .swiper-pagination::v-deep .swiper-pagination-bullet {
    width: 13px !important;
    border-radius: 20px;
    height: 3px;
    opacity: 0.3;
    margin: 0 3px;
    background-color: #fff;
    @media (max-width: 600px) {
      height: 2px;
    }
  }
  .swiper-pagination::v-deep .swiper-pagination-bullet-active {
    opacity: 1;
    background-color: #fff;
  }
  .swiper-button-prev::after {
    display: none;
  }
  .swiper-button-next::after {
    transform: scale(0);
    display: none;
  }
  .swiper-button-prev {
    background-color: $color-2;
    border-radius: 50%;
    width: 35px;
    height: 35px;
    transition: all 0.5s ease;
    // box-shadow: 0 0 1px 2px rgba(128, 128, 128, 0.449);
  }
  .swiper-button-next {
    background-color: $color-2;
    border-radius: 50%;
    width: 35px;
    height: 35px;
    transition: all 0.5s ease;
    // box-shadow: 0 0 1px 2px rgba(128, 128, 128, 0.449);
  }
  .icon {
    font-size: 27px !important;
    color: rgb(255, 255, 255);
    font-weight: bold;
  }
  ::v-deep.swiper-button-next.swiper-button-disabled {
    opacity: 0;
    transform: translatex(-50px);
  }
  ::v-deep.swiper-button-prev.swiper-button-disabled {
    opacity: 0;
    transform: translatex(50px);
  }
  ::v-deep.swiper-container {
    @media (max-width: 600px) {
      padding-right: 5px;
      padding-left: 5px;
    }
  }
}
::v-deep .v-image.v-responsive.theme--light {
  height: 330px !important;
  @media (max-width: 600px) {
    height: 180px !important;
  }
}
.AdvertisementTow {
  height: 330px !important;
  @media (max-width: 600px) {
    border-radius: 0px !important;
    height: 180px !important;
  }
}
::v-deep.swiper-pagination.swiper-pagination-clickable.swiper-pagination-bullets {
  bottom: 0;
}
</style>
