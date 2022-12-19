<template>
  <div class="StoreVoucher">
    <v-card-title class="titel"> قسائم المتجر </v-card-title>

    <swiper class="swiper" :options="swiperOption">
      <swiper-slide v-for="n in 10" :key="n">
        <v-card
          flat
          style="border: 2px dashed #ffd54f !important"
          color="amber lighten-5"
          class=" "
        >
          <v-row no-gutters>
            <v-col>
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
            <v-col style="margin: auto 0; text-align: center" cols="3">
              <v-btn small dark class="deep-orange btn lighten-1" elevation="0">
                أخذ
              </v-btn>
            </v-col>
          </v-row>
        </v-card>
      </swiper-slide>
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
        freeMode: true,
        effect: "cards",
        spaceBetween: 10,
        autoplay: {
          delay: 20000,
          disableOnInteraction: false,
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
    font-size: 15px !important;
    font-weight: 600 !important;
    padding: 0 6px !important ;
    min-width: 30px !important;

    @media (max-width: 600px) {
      font-size: 13px !important;
      min-width: 25px !important;
    }
    @media (max-width: 400px) {
      font-size: 12px !important;
      min-width: 22px !important;
    }
  }
}
::v-deep .col.col-4 {
  @media (max-width: 600px) {
    flex: 0 0 100%;
    max-width: 100%;
    padding: 10px 0 !important;
  }
}
</style>
