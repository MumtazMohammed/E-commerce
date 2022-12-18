<template>
  <div class="Shape_box">
    <v-container class="pa-0">
      <div class="Card-box">
        <v-sheet rounded=" ">
          <div class="pa-3 d-flex font-weight-bold tital">
            فئة
            <strong class="mx-1">الخدمات</strong>
          </div>
          <v-card flat class="px-1">
            <swiper class="swiper" :options="swiperOption">
              <swiper-slide
                class="mt-5"
                v-for="Servic in Services"
                :key="Servic.ServicId"
              >
                <v-card
                  to="/ServicesPage"
                  color="#eee"
                  class="d-flex ServiceCard align-center justify-space-between flex-column"
                >
                  <v-icon class="icon">
                    {{ Servic.ServicIcon }}
                  </v-icon>
                  <span class="grey--text ServiceText py-3 text-center">
                    {{ Servic.ServicText }}
                  </span>
                </v-card>
              </swiper-slide>
            </swiper>
          </v-card>
        </v-sheet>
      </div>
      <div class="card-box-small pb-3">
        <v-card class="mx-auto my-3 info-card" max-width="95%">
            <v-row no-gutters>
              <v-col style="border-left: 2px solid #fff" cols="6" class="pa-0">
                <v-card-title class="pa-1 text">
                  <v-icon color="yellow accent-4" class="info-icon" size="22">
                    mdi-alpha-s-circle-outline
                  </v-icon>
                  <span class="">0</span>
                  نقطة
                </v-card-title>
              </v-col>
              <v-col cols="6" class="pa-0">
                <v-card-title class="pa-1 text">
                  <v-icon color="amber darken-2" class="info-icon" size="22">
                    mdi-ticket-percent-outline
                  </v-icon>
                  <span class="">0</span>
                  قسائم
                </v-card-title>
              </v-col>
            </v-row>
        </v-card>
        <div class="pt-2 d-flex font-weight-bold tital">
          فئة
          <strong class="mx-1">الخدمات</strong>
        </div>
        <v-card flat tile class="px-1">
          <swiper class="swiper" :options="swiperOption">
            <swiper-slide
              class="mt-5"
              v-for="Servic in Services"
              :key="Servic.ServicId"
            >
              <v-card
                to="/ServicesPage"
                color="#eee"
                class="d-flex ServiceCard align-center justify-space-between flex-column"
              >
                <v-icon class="icon">
                  {{ Servic.ServicIcon }}
                </v-icon>
                <span class="grey--text ServiceText py-3 text-center">
                  {{ Servic.ServicText }}
                </span>
              </v-card>
            </swiper-slide>
          </swiper>
        </v-card>
      </div>
    </v-container>
  </div>
</template>

<script>
import CarShape from "../data-json/CarShape.json";
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";
export default {
  name: "CarShape",
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      Tital: "تصفح السيارات حسب شكل المركبة",
      CarShape,
      swiperOption: {
        initialSlide: 0,
        freeMode: true,
        effect: "card",
        spaceBetween: 13,
        autoplay: {
          delay: 20000,
          disableOnInteraction: false,
          stopOnLastSlide: true,
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
          1000: {
            slidesPerView: 8,
            slidesPerGroup: 8,
          },
          769: {
            slidesPerView: 6,
            slidesPerGroup: 6,
          },
          768: {
            slidesPerView: 3,
            slidesPerGroup: 3,
          },
          640: {
            slidesPerView: 5,
            slidesPerGroup: 5,
          },
          499: {
            slidesPerView: 5,
            slidesPerGroup: 5,
          },
          498: {
            slidesPerView: 4,
            slidesPerGroup: 4,
          },

          381: {
            slidesPerView: 4,
            slidesPerGroup: 4,
          },
          380: {
            slidesPerView: 3,
            slidesPerGroup: 3,
          },
          250: {
            slidesPerView: 3,
            slidesPerGroup: 3,
          },
        },
      },
      Services: [
        {
          ServicId: 1,
          ServicText: "خدمة هندسية",
          ServicIcon: "mdi-wrench-cog-outline",
          ServicColor: "red--text text--darken-1",
        },
        {
          ServicId: 2,
          ServicText: "خدمة برمجية",
          ServicIcon: "mdi-blender-software",
          ServicColor: "blue--text text--darken-2",
        },
        {
          ServicId: 3,
          ServicText: "خدمة عقارية",
          ServicIcon: "mdi-home-group",
          ServicColor: "",
        },
        {
          ServicId: 3,
          ServicText: "خدمة توصيل",
          ServicIcon: "mdi-moped",
          ServicColor: "",
        },
        {
          ServicId: 5,
          ServicText: " شقق وفنادق",
          ServicIcon: "mdi-home-city-outline",
          ServicColor: "cyan--text text--accent-4",
        },
        {
          ServicId: 6,
          ServicText: " السفر والسياحة",
          ServicIcon: "mdi-plane-train",
          ServicColor: "deep-orange--text",
        },
        {
          ServicId: 7,
          ServicText: "تأجير مركبات",
          ServicIcon: "mdi-car-key",
          ServicColor: "yellow--text text--darken-4",
        },
        {
          ServicId: 8,
          ServicText: "الصيانة",
          ServicIcon: "mdi-tools",
          ServicColor: "grey--text text--accent-3",
        },
        {
          ServicId: 9,
          ServicText: " خدمات اخرى",
          ServicIcon: "mdi-filter-variant",
          ServicColor: "amber--text text--accent-3",
        },
      ],
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

.Shape_box {
  // padding-bottom: 25px;
  display: flex;
  justify-content: center;
  width: 100%;
  position: relative;

  .tital {
    font-family: $fontfamliy2;
    font-size: 18px;
    color: $fontcolorlinks;
    letter-spacing: 0px !important;
    justify-content: center;

    @media (max-width: 470px) {
      font-size: 16px;
    }
    @media (max-width: 350px) {
      font-size: 14px;
    }
  }
  strong {
    color: $color-2;
  }
  .ServiceText {
    font-family: $fontfamliy3;
    font-size: 14px;
    font-weight: 600;
    letter-spacing: 0;
    color: #474747a3 !important;
    @media (max-width: 750px) {
      font-size: 13px;
    }
  }
  .icon {
    font-size: 20px;
    background-color: #eee;
    padding: 6px;
    width: 30px;
    height: 30px;
    border-radius: 50% !important;
    color: #fc614dea;
    position: relative;
    z-index: 2;
    box-shadow: 0px 0px 0px 6px rgb(255, 255, 255);
    // border: 1px solid ;
    margin-top: -16px !important;

    // box-shadow: 0px 0px 5px 0px $fontcolorlinks;
    @media (max-width: 750px) {
      font-size: 17px;
      width: 17px;
      height: 17px;
      margin-top: -14.5px !important;
      box-shadow: 0px 0px 0px 4px rgb(255, 255, 255);
    }
  }
  .text {
    font-family: $fontfamliy3 !important;
    font-size: 13.5px !important;
    letter-spacing: 0 !important;
    justify-content: space-evenly;
    color: $color-2;
    font-weight: 600;
    span {
      color: $fontcolorlinks;
    }
  }
  .ServiceCard {
    position: relative;
  }
}

.Card-box {
  // border: 1px solid grey;
  padding: 10px;
  display: none;
  @media (min-width: 600px) {
    padding: 0px;
    display: block;
  }
}
.card-box-small {
  display: none;
  position: relative;
  z-index: 5;
  @media (max-width: 600px) {
    display: block;
  }
}
// swiper
.swiper {
  // height: 100px !important;
  padding: 10px 0 !important;
  @media (max-width: 600px) {
    padding-top: 17.5px !important;
  }
}
::v-deep .container.pt-0 {
  @media (max-width: 750px) {
    padding: 0 !important;
  }
}
::v-deep .swiper-slide {
  margin: 0 5.5px !important;
  @media (max-width: 600px) {
    margin: 0 4.3px !important;
  }
}
::v-deep .v-sheet.v-card:not(.v-sheet--outlined) {
  @media (max-width: 750px) {
    // box-shadow: none;
  }
}
.info-card {
  background-color: #f5f5f5 !important;
  .info-icon {
    background-color: #fff;
    border-radius: 50%;
    padding: 2px;
  }
}
</style>
