<template>
  <div class="BestOffer py-2">
    <v-container class="container py-0">
      <v-row no-gutters>
        <v-col sm="6" class="my-auto">
          <div class="pa-3 d-flex font-weight-bold tital">
            الأعلى
            <strong class="mx-1">مبيعاً</strong>
          </div>
        </v-col>
        <v-col sm="6" class="my-auto">
          <v-chip-group
            v-model="chip"
            class="filter-sale pl-2"
            active-class="filter-sale-active "
          >
            <v-chip small> في اليوم </v-chip>
            <v-chip small> في الأسبوع </v-chip>
            <v-chip small> في الشهر </v-chip>
          </v-chip-group>
        </v-col>
      </v-row>

      <!-- <span class="line my-3 mx-auto"></span> -->
      <swiper class="swiper pt-2" :options="swiperOption">
        <swiper-slide v-for="(Product, index) in VerifiedCar" :key="index">
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
            min-height="200"
            
            color=" transparent"
            style="overflow: hidden; position: relative"
          >
            <v-img
              contain
              height="170"
              class="blue-grey lighten-3"
              style="overflow: hidden;"
              :src="getimageUrl(Product.folder, Product.image)"
            >
              <v-card
                class="img-cover"
                :img="getimageUrl(Product.folder, Product.image)"
                width="100%"
                height="100%"
              ></v-card>
            </v-img>
            <v-card-actions class="justify-center">
              <v-chip
                style="background-color: #fc624d; color: white"
                class="filter-sale"
                small
              >
                484
                <span class="mr-1">في اليوم</span>
              </v-chip>
            </v-card-actions>
            <!-- <v-card-text
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
            </v-card-actions> -->
          </v-card>
        </swiper-slide>
        <!-- <swiper-slide>
          <v-card
            flat
            max-width="190px"
            height="240px"
            router
            color="transparent"
            class="overflow-hidden d-flex flex-column justify-center align-center"
          >
            <v-card-text class="text-center py-1 card-text-seeMore">
              الكل
            </v-card-text>
            <v-icon size="17" class="deep-orange--text text--darken-1"
              >mdi-plus</v-icon
            >
          </v-card>
        </swiper-slide> -->
        <div class="swiper-pagination" slot="pagination"></div>
      </swiper>
    </v-container>
  </div>
</template>

<script>
import VerifiedCar from "../data-json/All-Car.json";
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";
export default {
  name: "BestOffer",
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      chip: 0,
      VerifiedCar,
      carName: this.$route.params.carName,
      carId: this.$route.params.carId,
      CarShape: this.$route.params.CarShape,
      Company: this.$route.params.Company,
      swiperOption: {
        freeMode: false,
        effect: "cards",
        slidesPerColumn: 2,
        spaceBetween: 5,
        autoplay: false,
        loop: false,
        loopFillGroupWithBlank: false,
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
          dynamicBullets: true,
          type: "progressbar",
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
            slidesPerView: 4,
            slidesPerGroup: 4,
          },
          470: {
            slidesPerView: 3,
            slidesPerGroup: 3,
          },
          250: {
            slidesPerView: 3,
            slidesPerGroup: 3,
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
.BestOffer {
  width: 100%;
  min-height: 40vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: $color-background;
  // font-family: $fontfamliy;
  strong {
    color: $color-2;
  }
  .filter-sale {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    color: #fff !important;
  }
  .filter-sale-active {
    background-color: $color-2 !important;
    color: #fff !important;
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
    color: $fontcolor;
  }
  .tital {
    font-family: $fontfamliy2;
    font-size: 18px;
    color: $fontcolorlinks;
    letter-spacing: 0px !important;
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

::v-deep i.v-icon.notranslate.material-icons.theme--light {
  color: $color-2;
  font-size: 28px;
  font-weight: 600;
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
  font-size: 13px !important;
  text-decoration: line-through;
}
.PriceAfter {
  font-size: 14px !important;
  display: block;
  text-align: left;
  color: $color-2;
}

//
.swiper {
  height: 470px;
  margin-left: auto;
  margin-right: auto;

  .swiper-slide {
    height: 200px;
    // margin: 1px !important;
    margin-bottom: 15px !important;
  }
}
::v-deep .swiper-container-horizontal > .swiper-pagination-progressbar {
  top: 455px !important;
  width: 50px;
  height: 5px;
  left: 50%;
  transform: translateX(-50%);
  border-radius: 5px;
  overflow: hidden;
  background-color: #eee;

  span.swiper-pagination-progressbar-fill {
    background-color: $color-2;
    box-shadow: inset 0 0 0 0.2px #eee;
  }
}
::v-deep .swiper-wrapper {
  // width: auto !important;
}
::v-deep.swiper-container {
  padding-right: 5px;
  padding-left: 5px !important;
}
::v-deep .v-slide-group__content {
  justify-content: end;
}
::v-deep .v-chip .v-chip__content {
  // align-items: flex-start;
}
.img-cover {
  position: relative;
  z-index: -2;
  // overflow: hidden;
}
.img-cover::before {
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: #171717c1;
}
</style>
