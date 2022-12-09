<template>
  <div class="FeaturedProducts">
    <!-- <span class="line my-3 mx-auto"></span> -->
    <swiper class="swiper" :options="swiperOption">
      <swiper-slide v-for="(Product, index) in getCarInfo" :key="index">
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
          max-width="190px"
          height="230px"
          router
          class="overflow-hidden"
        >
          <div class="best-price-tag">
            <small class="discountPercent">
              {{ Product.discountPercent }}-
            </small>
          </div>

          <v-img
            height="120"
            full-width
            :src="getimageUrl(Product.folder, Product.image)"
          ></v-img>
          <v-card-text class="d-inline-block card-text pb-0 pa-2 text-truncate">
            {{ Product.name }} {{ Product.company }}
          </v-card-text>
          <strong
            class="red--text text--lighten-3 price-befor px-2 text-truncate"
          >
            {{ Product.payment }}
            <small class="text-truncate">ريال</small>
          </strong>
          <v-spacer></v-spacer>
          <strong
            class="red--text text--lighten-2 new-price px-2 text-truncate"
          >
            {{ Product.payment }}
            <small class="text-truncate">ريال</small>
          </strong>
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
      <!-- <div class="swiper-button-prev hidden-sm-and-down" slot="button-prev">
            <v-icon class="icon">mdi-chevron-right</v-icon>
          </div>
          <div class="swiper-button-next hidden-sm-and-down" slot="button-next">
            <v-icon class="icon">mdi-chevron-left</v-icon>
          </div> -->
    </swiper>
  </div>
</template>

<script>
import VerifiedCar from "../data-json/All-Car.json";
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";
export default {
  name: "FeaturedProducts",
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
          delay: 50000,
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
.FeaturedProducts {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: $color-background;
  font-family: $fontfamliy;
  strong {
    color: $color-2;
  }
  .swiper {
    height: 270px !important;

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

    ::v-deep.swiper-container {
      @media (max-width: 600px) {
        padding-right: 5px;
        padding-left: 5px;
      }
    }
    ::v-deep.swiper-slide.swiper-slide-active {
      margin-right: 5px;
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
    letter-spacing: 0px !important;
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
::v-deep .v-responsive__content {
  display: flex;
  justify-content: center;
  align-items: center;
}
.discountPercent {
  color: white !important;
  font-weight: 500;
  font-size: 15px;
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
.price-befor {
  text-decoration: line-through;
  font-size: 15px !important;
}
.new-price {
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
