<template>
  <div class="BestOffer">
    <v-app-bar class="mb-5" app hide-on-scroll>
      <v-toolbar-title class="toolbar-title">
        <v-icon size="20">mdi-history </v-icon>
        شوهدت مؤخرا
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/TheUserPageView" icon>
        <v-icon size="30">mdi-arrow-left-thin</v-icon>
      </v-btn>
    </v-app-bar>
    <v-container class="container py-0 mt-15">
      <v-row class="mt-3">
        <v-col
          cols="6"
          class="pa-1"
          v-for="(Product, index) in getCarInfo"
          :key="index"
        >
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
            <v-card-text
              class="d-inline-block card-text pb-0 pa-2 text-truncate"
            >
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
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import VerifiedCar from "../../data-json/All-Car.json";
// import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";
export default {
  name: "BestOffer",
  components: {
    // Swiper,
    // SwiperSlide,
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
        autoplay: false,
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
.BestOffer {
  width: 100%;
  min-height: 80vh;
  font-family: $fontfamliy;
  padding-bottom: 20px;
  strong {
    color: $color-2;
  }
  .toolbar-title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorlinks !important;
    font-size: 16px !important;
    font-weight: 600;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    .v-icon {
      color: $color-2 !important;
      margin-left: 5px;
    }
  }

  .card-text {
    font-family: $fontfamliy2;
    letter-spacing: 0;
    font-size: 15px;
    font-weight: 400;
    color: $fontcolor !important;
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
  z-index: 1;
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
</style>
