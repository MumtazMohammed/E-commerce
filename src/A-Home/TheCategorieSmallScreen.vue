<template>
  <div class="Registration">
    <v-container class="container">
      <v-card color="transparent" flat class="card-wrapping pt-2">
        <v-col>
          <div class="mb-2 ont-weight-bold tital">
            جميع
            <strong class="mx-1">الفئات</strong>
          </div>
        </v-col>
        <!-- <span class="line my-3 mx-auto"></span> -->
        <swiper class="swiper" :options="swiperOption">
          <swiper-slide v-for="(Categorie, index) in Categories" :key="index">
            <v-card
              max-width="190px"
              height="auto"
              color="transparent"
              class="overflow-hidden py-2"
            >
              <v-row
                no-gutters
                class="flex-column justify-center align-center pa-0"
              >
                <v-card flat color="transparent" to="/Products" router>
                  <v-card-actions
                    class="flex-column justify-center align-center pa-0"
                  >
                    <v-avatar size="85px" color="grey lighten-3">
                      <v-img
                        contain
                        :src="getimageUrl(Categorie.folder, Categorie.imgOne)"
                      ></v-img>
                    </v-avatar>

                    <v-card-text
                      class="px-0 pb-0 text-center card-text"
                      v-text="Categorie.titalOne"
                    >
                    </v-card-text>
                  </v-card-actions>
                </v-card>
                <v-card flat color="transparent" to="/Products" router>
                  <v-card-actions
                    class="flex-column justify-center align-center pa-0"
                  >
                    <v-avatar size="85px" color="grey lighten-3">
                      <v-img
                        contain
                        :src="getimageUrl(Categorie.folder, Categorie.imgTow)"
                      ></v-img>
                    </v-avatar>
                    <v-card-text
                      class="px-0 text-center card-text"
                      v-text="Categorie.titalTow"
                    >
                    </v-card-text>
                  </v-card-actions>
                </v-card>
              </v-row>
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
  name: "ShowVerifiedCar",
  title: "Loop mode with multiple slides per group",
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
      Categories: [
        {
          titalOne: "الجولات والأجهزة اللوحية ",
          imgOne: "mobile.png",
          titalTow: "كمبيوتر وملحقاتها",
          imgTow: "computing.png",
          folder: "categories",
        },
        {
          imgOne: "Fashion.png",
          imgTow: "health-beauty.png",
          folder: "categories",
          titalOne: "الأزياء",
          titalTow: "الصحة & الجمال",
        },
        {
          imgOne: "furniture.png",
          imgTow: "game.png",
          folder: "categories",
          titalOne: "اثاث منزلية & مكتبية ",
          titalTow: "ألعاب",
        },
        {
          imgOne: "grocery.png",
          imgTow: "baby.png",
          folder: "categories",
          titalOne: " البقالة",
          titalTow: " منتجات الأطفال",
        },
        {
          imgOne: "librry.png",
          imgTow: "Electricity.png",
          folder: "categories",
          titalTow: " البناء والكهرباء",
          titalOne: " القرطاسية ",
        },
        {
          imgOne: "vehicles.png",
          imgTow: "real-estates.png",
          folder: "categories",
          titalOne: "المركبات",
          titalTow: " عقارات",
        },
      ],
      swiperOption: {
        initialSlide: 0,
        freeMode: false,
        effect: "cards",
        spaceBetween: 8,
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
.Registration {
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
    height: 380px !important;
    padding: 10px;

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

  .container {
    @media (max-width: 950px) {
      padding-left: 0px !important;
      padding-right: 0px !important;
    }
  }
  .card-text {
    font-family: $fontfamliy3;
    letter-spacing: 0;
    font-size: 14px;
    font-weight: 600;
    color: $fontcolorlinks !important;
    height: 40px !important;
  }
  .tital {
    position: relative;
    text-align: center;
    font-family: $fontfamliy3;
    font-size: 20px;
    color: $fontcolorlinks;
    font-weight: 600;
    @media (max-width: 400px) {
      font-size: 18px;
    }
    store {
      color: $color-2;
    }
  }
  .tital::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 0;
    opacity: 0.9;
    background-color: #eee;
    width: 40%;
    height: 2.2px;
    @media (max-width: 850px) {
      width: 35%;
    }
    @media (max-width: 650px) {
      width: 30%;
    }
    @media (max-width: 430px) {
      width: 26% !important;
    }
  }
  .tital::after {
    content: "";
    position: absolute;
    top: 50%;
    right: 0;
    opacity: 0.9;
    background-color: #eee;
    width: 40%;
    height: 2.2px;
    @media (max-width: 850px) {
      width: 35%;
    }
    @media (max-width: 650px) {
      width: 30%;
    }
    @media (max-width: 430px) {
      width: 26%;
    }
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
</style>
