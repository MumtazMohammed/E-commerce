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
            <v-row
              no-gutters
              class="flex-column justify-center align-center pa-0"
            >
              <v-card
                min-width="150px"
                max-width="180px"
                outlined
                class="pa-2 my-1"
                to="/Products"
                router
              >
                <v-card-actions
                  class="flex-column justify-center align-center pa-0"
                >
                  <v-avatar size="90px" tile>
                    <v-img
                      contain
                      :src="getimageUrl(Categorie.folder, Categorie.imgOne)"
                    ></v-img>
                  </v-avatar>

                  <v-card-text
                    class="px-0 py-2 text-center card-text"
                    v-text="Categorie.titalOne"
                  >
                  </v-card-text>
                </v-card-actions>
              </v-card>
              <v-card
                min-width="150px"
                max-width="180px"
                outlined
                class="pa-2 my-1"
                to="/Products"
                router
              >
                <v-card-actions
                  class="flex-column justify-center align-center pa-0"
                >
                  <v-avatar size="90px" tile>
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
    height: 405px !important;
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
    @media (max-width: 600px) {
      font-size: 16px;
    }
    @media (max-width: 350px) {
      font-size: 14px;
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
</style>
