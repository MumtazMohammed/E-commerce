<template>
  <div class="DailyOffer">
    <v-card flat class="card-wrapping" color="transparent">
      <div class="pa-3 mb-2 d-flex font-weight-bold tital">
        من نفس
        <strong class="mx-1">البائع</strong>
      </div>

      <swiper class="swiper" :options="swiperOption">
        <swiper-slide v-for="(Product, index) in getCarInfo" :key="index">
          <v-card
            :to="{
              name: 'ViewCar',
              params: {
                carName: Product.name,
                carShape: Product.Shape,
                carId: Product.id,
                Company: Product.folder,
              },
            }"
            max-width="190px"
            height="230px"
            router
            class="overflow-hidden"
          >
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
            <strong class="red--text price text--lighten-2 px-2 text-truncate">
              {{ Product.payment }}
              <small class="text-truncate">ريال</small>
            </strong>
            <v-card-actions class="justify-space-between pt-1 pa-0">
              <div class="discount-tag">
                <span>9%</span>
              </div>
              <p class="ma-0 sold-info px-2 text-truncate">
                باع {{ Product.id }}
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
        <div class="swiper-button-prev hidden-sm-and-down" slot="button-prev">
          <v-icon class="icon">mdi-chevron-right</v-icon>
        </div>
        <div class="swiper-button-next hidden-sm-and-down" slot="button-next">
          <v-icon class="icon">mdi-chevron-left</v-icon>
        </div>
      </swiper>
    </v-card>
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
      padding-left: 5px;
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
    font-family: $fontfamliy2;
    letter-spacing: 0;
    font-size: 15px;
    font-weight: 400;
    color: $fontcolor !important;
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

::v-deep .v-slide-group__next {
  align-items: center;
  display: flex;
  flex: 0 1 30px;
  justify-content: flex-end;
  min-width: 30px;
  @media (max-width: 950px) {
    display: none;
  }
}
::v-deep .v-slide-group__prev {
  align-items: center;
  display: flex;
  flex: 0 1 30px;
  justify-content: flex-start;
  min-width: 30px;
  @media (max-width: 950px) {
    display: none;
  }
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
  font-size: 13px !important;
  font-weight: 500 !important;
  color: grey !important;
  display: flex;
  justify-content: center;
  align-items: center;
  span {
    font-size: 14px !important;
    background-color: $color-2;
    padding: 5px;
    width: 15px;
    height: 15px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-right: 2px;
    color: rgb(255, 255, 255) !important;
  }
}
.price {
  font-size: 15px !important;
}
.card-text-seeMore {
  font-family: $fontfamliy3;
  letter-spacing: 0;
  font-size: 16px;
  font-weight: 600;
  color: $fontcolorlinks !important;
}
</style>
