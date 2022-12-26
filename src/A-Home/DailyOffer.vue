<template>
  <div class="DailyOffer">
    <v-container class="container py-0">
      <v-card class="card-wrapping" flat color="transparent">
        <div class="pa-3 pt-0 mb-2 d-flex font-weight-bold tital">
          عروضات
          <strong class="mx-1">يومية</strong>
          لا
          <strong class="mx-1">تفوتها</strong>
        </div>

        <swiper class="swiper" :options="swiperOption">
          <swiper-slide v-for="(Product, index) in getCarInfo" :key="index">
            <div style="position: relative">
              <h1 class="ribbon">متميز</h1>
              <v-card
                :to="{
                  name: 'ShowTheProduct',
                  params: {
                    carName: Product.name,
                    carShape: Product.Shape,
                    carId: Product.id,
                    Company: Product.folder,
                  },
                }"
                width="100%"
                min-height="220"
                style="overflow: hidden"
                flat
                tile
                color="transparent"
              >
                <div v-if="Product.discountPercent" class="best-price-tag">
                  <small class="discountPercent">
                    {{ Product.discountPercent }}-
                  </small>
                </div>
                <v-img
                  height="170"
                  :src="getimageUrl(Product.folder, Product.image)"
                ></v-img>
                <v-card-text
                  class="d-inline-block card-text py-0 pa-2 text-truncate"
                >
                  {{ Product.name }} {{ Product.company }}
                </v-card-text>
                <v-card-actions class="py-0 justify-space-between">
                  <strong
                    class="grey--text text--lighten-1 PriceBefore text-truncate"
                  >
                    {{ Product.payment }}
                    <small class="text-truncate">ريال</small>
                  </strong>
                  <strong class="PriceAfter text-truncate">
                    {{ Product.payment }}
                    <small class="text-truncate">ريال</small>
                  </strong>
                </v-card-actions>
                <v-card-actions class="py-1 justify-space-between">
                  <p class="ma-0 sold-info px-2 text-truncate">
                    <span>{{ Product.id }} </span>بيعت
                  </p>
                  <span class="card-text grey--text px-2">
                    {{ Product.location }}
                  </span>
                </v-card-actions>
              </v-card>
            </div>
          </swiper-slide>
          <swiper-slide>
            <v-card
              flat
              max-width="190px"
              height="240px"
              color="transparent"
              router
              class="overflow-hidden d-flex flex-column justify-center align-center"
            >
              <v-card-text class="text-center py-1 card-text-seeMore">
                الكل
              </v-card-text>
              <v-icon size="17" class="deep-orange--text text--darken-1">
                mdi-plus
              </v-icon>
            </v-card>
          </swiper-slide>
          <div class="swiper-pagination" slot="pagination"></div>
        </swiper>
      </v-card>
    </v-container>
  </div>
</template>

<script>
import VerifiedCar from "../data-json/All-Car.json";
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";
export default {
  name: "DailyOffer",
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      VerifiedCar,
      carName: this.$route.params.carName,
      carId: this.$route.params.carId,
      CarShape: this.$route.params.CarShape,
      Company: this.$route.params.Company,
      swiperOption: {
        initialSlide: 0,
        freeMode: false,
        effect: "cards",
        spaceBetween: 10,
        autoplay: false,
        loop: false,
        loopFillGroupWithBlank: false,
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
          dynamicBullets: true,
        },
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev",
        },
        breakpoints: {
          1024: {
            slidesPerView: 6,
            slidesPerGroup: 6,
          },
          768: {
            slidesPerView: 5,
            slidesPerGroup: 5,
          },
          640: {
            slidesPerView: 4,
            slidesPerGroup: 4,
          },
          471: {
            slidesPerView: 3,
            slidesPerGroup: 3,
          },
          470: {
            slidesPerView: 3,
            slidesPerGroup: 3,
          },
          250: {
            slidesPerView: 2,
            slidesPerGroup: 2,
          },
        },
      },
    };
  },
  // this is help full to call the image inside folder and inject to the src
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
  computed: {
    getCarInfo() {
      let GetCarVerified = [];
      for (let i = 0; i < this.VerifiedCar.length; i++) {
        if (this.VerifiedCar[i].Vip == true) {
          GetCarVerified.push(this.VerifiedCar[i]);
        }
      }
      return GetCarVerified;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.DailyOffer {
  width: 100%;
  min-height: 40vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: $color-background;
  font-family: $fontfamliy;

  strong {
    color: $color-2;
  }
  .swiper {
    height: auto;
    padding-bottom: 45px;
    padding-right: 5px !important;
    ::v-deep.swiper-pagination-bullet {
      font-size: 10px;
      width: 9px !important;
      height: 9px !important;
      line-height: 1.5;
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
  ::v-deep.swiper-container {
    @media (max-width: 600px) {
      padding-right: 5px;
      padding-left: 5px !important;
    }
  }

  .v-sheet {
    @media (max-width: 950px) {
      padding-left: 0px !important;
      padding-right: 0px !important;
    }
  }

  .container {
    @media (max-width: 950px) {
      padding-left: 0px !important;
      padding-right: 0px !important;
    }
  }
  .tital {
    font-family: $fontfamliy2;
    font-size: 18px;
    color: $fontcolorlinks;
    pointer-events: none;

    @media (max-width: 470px) {
      font-size: 16px;
    }
    @media (max-width: 350px) {
      font-size: 14px;
    }
  }
  a {
    font-size: 13px;
  }
}
::v-deep .v-responsive__content {
  display: flex;
  justify-content: center;
  align-items: center;
}

::v-deep i.v-icon.notranslate.material-icons.theme--light {
  color: $color-2;
  font-size: 28px;
  font-weight: 600;
}

.card-text-seeMore {
  font-family: $fontfamliy3;
  letter-spacing: 0;
  font-size: 16px;
  color: $fontcolorlinks !important;
}
// Products
.sold-info {
  font-family: $fontfamliy3 !important;
  font-size: 13px !important;
  font-weight: 600 !important;
  color: $fontcolorlinks;
  span {
    color: $color-2 !important;
    margin-left: 5px;
    font-size: 14px !important;
    letter-spacing: 1.5px !important;
  }
}
.card-text {
  font-family: $fontfamliy3 !important;
  color: $fontcolor;
  letter-spacing: 0 !important;
  font-size: 13px !important;
}
.PriceBefore {
  font-size: 14px !important;
  text-decoration: line-through;
}
.PriceAfter {
  font-size: 15px !important;
  display: block;
  text-align: left;
  color: $color-2;
}
.best-price-tag {
  position: absolute;
  left: 4px;
  top: 0px;
  clip-path: polygon(
    50% 0%,
    100% 0,
    100% 35%,
    100% 70%,
    100% 100%,
    49% 70%,
    0 100%,
    0% 70%,
    0% 35%,
    0 0
  );

  background-color: $color-2;
  width: 35px;
  height: 40px;
  display: flex;
  justify-content: center;
  // transform: rotate(360deg);
  z-index: 5;
  border-radius: 0 !important;
}
.discountPercent {
  color: white !important;
  font-weight: 500;
  font-size: 13px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 10px;
}

//
.ribbon {
  position: absolute;
  top: 3px;
  right: 0;
  z-index: 15;
  width: 50px;
  text-align: center;
  font-size: 11px;
  color: #ffffff;
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  border-radius: 5px 0px 0px 5px !important;
  background: $color-2;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.5);
}

.ribbon:before,
.ribbon:after {
  position: absolute;
  content: "";
  display: block;
}

.ribbon:before {
  width: 0.469em;
  height: 100%;
  padding: 0 0 0.438em;
  top: 0;
  right: -0.469em;
  background: inherit;
  border-radius: 0px 5px 5px 0px !important;
}

.ribbon:after {
  width: 0.313em;
  height: 0.313em;
  background: rgba(0, 0, 0, 0.35);
  bottom: -0.313em;
  right: -0.314em;
  border-radius: 0px 5px 5px 0px !important;
  box-shadow: inset -1px 2px 2px rgba(0, 0, 0, 0.3);
}
</style>
