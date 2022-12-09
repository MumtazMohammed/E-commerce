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
              height="230px"
              color="transparent"
              style="overflow: hidden"
            >
              <div v-if="Product.discountPercent" class="best-price-tag">
                <small class="discountPercent">
                  {{ Product.discountPercent }}-
                </small>
              </div>
              <v-img
                height="120"
                full-width
                :src="getimageUrl(Product.folder, Product.image)"
              ></v-img>
              <v-card-text
                class="d-inline-block card-text pb-0 pa-2 text-truncate"
              >
                {{ Product.name }} {{ Product.company }}
              </v-card-text>
              <!-- <v-card-actions class="pa-0"> -->
              <strong class="grey--text PriceBefore px-2 text-truncate">
                {{ Product.payment }}
                <small class="text-truncate">ريال</small>
              </strong>
              <strong class="PriceAfter px-2 text-truncate">
                {{ Product.payment }}
                <small class="text-truncate">ريال</small>
              </strong>
              <!-- </v-card-actions> -->
              <v-spacer></v-spacer>
              <v-card-actions class="justify-space-between pt-1 pa-0">
                <p class="ma-0 sold-info px-2 text-truncate">
                  <span>{{ Product.id }} </span>بيعت
                </p>
              </v-card-actions>
            </v-card>
          </swiper-slide>
          <swiper-slide>
            <v-card
              flat
              max-width="190px"
              height="230px"
              router
              class="overflow-hidden d-flex flex-column justify-center align-center"
            >
              <v-card-text class="text-center py-1 card-text-seeMore">
                الكل
              </v-card-text>
              <v-icon class="deep-orange--text text--darken-1">mdi-plus</v-icon>
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
    height: 290px !important;
    padding: 0 8px !important;

    .swiper-pagination::v-deep .swiper-pagination-bullet {
      width: 13px !important;
      border-radius: 30px;
      height: 4px;
      opacity: 0.3;
      margin: 0 2px;
      background-color: $color-3;
    }
    .swiper-pagination::v-deep .swiper-pagination-bullet-active {
      width: 20px !important;
      height: 4px;
      opacity: 1;
      background-color: $color-2;
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
  font-weight: 600;
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
  color: $fontcolor !important;
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
  width: 45px;
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
  font-size: 14px;
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
