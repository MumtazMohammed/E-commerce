<template>
  <div class="DailyOffer">
    <v-container flat class="card-wrapping" color="transparent">
      <div class="pa-3 mb-2 d-flex font-weight-bold tital">
        من نفس
        <strong class="mx-1">البائع</strong>
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
                full-width
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
            height="230px"
            router
            color="transparent"
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
        <div
          class="swiper-pagination swiper-pagination-bullets"
          slot="pagination"
        ></div>
      </swiper>
    </v-container>
  </div>
</template>

<script>
import VerifiedCar from "../data-json/All-Car.json";
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";
export default {
  name: "SameWonerProducts",
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
        effect: "cards",
        spaceBetween: 10,
        loop: false,
        loopFillGroupWithBlank: false,
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
          dynamicBullets: true,
          renderBullet(index, className) {
            return `<span class="${className} swiper-pagination-bullet-custom">${
              index + 1
            }</span>`;
          },
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
  background-color: transparent;
  strong {
    color: $color-2;
  }
  .swiper {
    height: 290px !important;
    padding: 0 10px;
    .swiper-pagination::v-deep .swiper-pagination-bullet {
      width: 9px !important;
      border-radius: 50%;
      height: 10px;
      opacity: 1;
      margin: 0 4px;
      background-color: #e0e0e0;
    }
    .swiper-pagination::v-deep .swiper-pagination-bullet-active {
      opacity: 1;
      background-color: $color-2;
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
  .card-text {
    font-family: $fontfamliy3;
    letter-spacing: 0;
    font-size: 13px;
  }
  .tital {
    font-family: $fontfamliy3;
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
.best-price-tag {
  position: absolute;
  left: 0px;
  top: 0px;
  z-index: 5;
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

.discount-tag {
  width: 45px;
  height: 20px;
  clip-path: polygon(25% 0%, 100% 0%, 100% 100%, 25% 100%, 10% 50%);
  background-color: $color-2;
  color: #fff !important;
  font-size: 15px;
  font-weight: 500;
  justify-content: start;
  padding-right: 1px;
}
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
.PriceBefore {
  font-size: 13px !important;
  text-decoration: line-through;
}
.PriceAfter {
  font-size: 14px !important;

  color: $color-2;
}
.card-text-seeMore {
  font-family: $fontfamliy3;
  letter-spacing: 0;
  font-size: 16px;
  color: $fontcolorlinks !important;
}
.ribbon {
  position: absolute;
  top: 3px;
  right: 0px;
  z-index: 15;
  padding: 0 5px;
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
.ribbon:before {
  content: "";
  position: absolute;
  display: block;
  width: 0.5em;
  height: 100%;
  padding: 0 0 5px 0px !important;
  top: 0;
  right: -0.51em;
  background: inherit;
  border-radius: 0px 5px 5px 0px !important;
}
.ribbon:after {
  position: absolute;
  content: "";
  display: block;
  width: 0.313em;
  height: 0.313em;
  background: rgba(0, 0, 0, 0.35);
  bottom: -0.313em;
  right: -0.3em;
  border-radius: 0px 5px 5px 0px !important;
  box-shadow: inset -1px 2px 2px rgba(0, 0, 0, 0.3);
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
</style>
