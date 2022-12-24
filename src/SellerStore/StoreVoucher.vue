<template>
  <div class="StoreVoucher">
    <v-card-title class="titel"> قسائم المتجر </v-card-title>

    <swiper class="swiper" :options="swiperOption">
      <swiper-slide v-for="n in 10" :key="n">
        <v-card
          flat
          style="border: 2px dashed #ffd54f !important"
          color="amber mx-1 lighten-5"
        >
          <v-row no-gutters>
            <v-col cols="12">
              <v-card-subtitle class="text pa-0 pr-1">
                خصم <span class="mx-1"><span>20</span>%</span>
              </v-card-subtitle>
              <v-card-text class="pa-0 pr-1 text">
                أنفق
                <span class="mx-1">
                  52<v-icon size="17">mdi-currency-rial</v-icon>
                </span>
                كحد أدنى
              </v-card-text>
              <v-card-text class="pa-0 pr-1 text">
                متاح حتى
                <span>10/2/2020</span>
              </v-card-text>
            </v-col>
            <v-col cols="12" class="py-1">
              <v-row no-gutters justify="center">
                <v-btn
                  width="83%"
                  small
                  dark
                  class="deep-orange btn lighten-1"
                  elevation="0"
                >
                  أخذ القسيمة
                </v-btn>
              </v-row>
            </v-col>
          </v-row>
        </v-card>
      </swiper-slide>
      <div
        class="swiper-pagination swiper-pagination-bullets"
        slot="pagination"
      ></div>
    </swiper>
  </div>
</template>
<script>
import Services from "../data-json/showroom.json";
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";
export default {
  name: "ServicesPage",
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      current: null,
      Services,
      swiperOption: {
        initialSlide: 0,
        freeMode: false,
        effect: "cards",
        spaceBetween: 0,
        autoplay: false,
        loop: false,
        loopFillGroupWithBlank: false,
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
          renderBullet(index, className) {
            return `<span class="${className} swiper-pagination-bullet-custom">${
              index + 1
            }</span>`;
          },
        },
        breakpoints: {
          1024: {
            slidesPerView: 4,
            slidesPerGroup: 4,
          },
          768: {
            slidesPerView: 3,
            slidesPerGroup: 3,
          },
          640: {
            slidesPerView: 2,
            slidesPerGroup: 2,
          },
          471: {
            slidesPerView: 2,
            slidesPerGroup: 2,
          },
          470: {
            slidesPerView: 2,
            slidesPerGroup: 2,
          },
          250: {
            slidesPerView: 2,
            slidesPerGroup: 2,
          },
        },
      },
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.StoreVoucher {
  background-color: $color-background;
  .titel {
    letter-spacing: 0 !important;
    font-size: 17px !important;
    font-weight: 500 !important;
    font-family: $fontfamliy3 !important;
    color: $fontcolor !important;
  }
  .text {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorlinks !important;
    @media (max-width: 600px) {
      font-size: 13px !important;
    }
  }
  .btn {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: #fff !important;
    font-size: 13px !important;
    margin: 0 auto !important;
    font-weight: 600;
    @media (max-width: 600px) {
      font-size: 13px !important;
    }
  }
}
.swiper {
  height: auto;
  padding-bottom: 45px;
  ::v-deep.swiper-pagination-bullet {
    font-size: 13px;
    width: 20px !important;
    height: 20px !important;
    line-height: 1.6;
    opacity: 0.5;
    background: rgb(223, 223, 223);
    transition: all 0.2s 0s linear;
    color: rgb(82, 82, 82);

    &:hover {
      opacity: 1;
    }

    &.swiper-pagination-bullet-active {
      opacity: 1;
      color: #fff;
      background: $color-2;
    }
  }
}
</style>
