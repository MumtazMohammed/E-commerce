<template>
  <div class="Registration py-2">
    <v-container class="py-0">
      <v-col class="py-1 pb-2">
        <div class="tital">
          جميع
          <strong class="mx-1">الفئات</strong>
        </div>
      </v-col>
      <!-- <span class="line my-3 mx-auto"></span> -->
      <swiper class="swiperR" :options="swiperOption">
        <swiper-slide v-for="(Categorie, index) in Categories" :key="index">
          <v-card
            min-width="100%"
            max-width="180px"
            color=""
            class="d-flex ServiceCard align-center justify-space-between flex-column"
            to="/Products"
            router
            flat
          >
            <v-avatar class="icon" size="60px" tile>
              <v-img
                contain
                :src="getimageUrl(Categorie.folder, Categorie.imgOne)"
              ></v-img>
            </v-avatar>

            <v-card-text
              class="pa-0 px-1 pt-2 text-center card-text"
              v-text="Categorie.titalOne"
            >
            </v-card-text>
          </v-card>
          <v-card
            min-width="100%"
            class="d-flex mt-3 ServiceCard align-center justify-space-between flex-column"
            to="/Products"
            router
            flat
            color=""
          >
            <v-avatar class="icon" size="60px" tile>
              <v-img
                contain
                :src="getimageUrl(Categorie.folder, Categorie.imgTow)"
              ></v-img>
            </v-avatar>
            <v-card-text
              class="pa-0 px-1 pt-2 text-center card-text"
              v-text="Categorie.titalTow"
            >
            </v-card-text>
          </v-card>
        </swiper-slide>
        <div
          class="swiper-pagination swiper-pagination-bullets"
          slot="pagination"
        ></div>
      </swiper>

      <v-col class="py-1 pb-2">
        <div class="tital">
          فئة
          <strong class="mx-1">الخدمات</strong>
        </div>
      </v-col>
      <!-- <swiper class="swiper" :options="swiperOption">
        <swiper-slide v-for="Servic in Services" :key="Servic.ServicId">
          <v-card
            color=""
            class="d-flex mt-3 ServiceCard align-center justify-space-between flex-column"
            to="/Products"
            router
            flat
          >
            <v-icon class="icon">
              {{ Servic.ServicIcon }}
            </v-icon>

            <v-card-text
              class="pa-0 px-1 py-2 text-center ser-text"
              v-text="Servic.ServicText"
            >
            </v-card-text>
          </v-card>
        </swiper-slide>
        <div class="swiper-pagination" slot="pagination"></div>
      </swiper> -->
      <v-row no-gutters>
        <v-col class="pa-1" v-for="Servic in Services" :key="Servic.ServicId">
          <v-card
            style="width: 100%"
            to="/Products"
            color="#eee"
            rounded="lg"
          >
            <!-- <v-icon left> {{ Servic.ServicIcon }} </v-icon> -->
            <!-- <v-spacer></v-spacer> -->
            <v-card-text
              class="pa-2 text-center ser-text"
              v-text="Servic.ServicText"
            >
            </v-card-text>
          </v-card>
          <!-- <v-card
            class="d-flex ServiceCard align-center justify-space-between flex-column"
            to="/Products"
            router
            flat
            rounded="lg"
          >
            <v-icon class="icon">
              {{ Servic.ServicIcon }}
            </v-icon>
            <v-card-text
              class="pa-0 px-1 py-2 text-center ser-text"
              v-text="Servic.ServicText"
            >
            </v-card-text>
          </v-card> -->
        </v-col>
      </v-row>
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
      Services: [
        {
          ServicId: 1,
          ServicText: "الخدمات الهندسية",
          ServicIcon: "mdi-wrench-cog-outline",
          ServicColor: "red--text text--darken-1",
        },
        {
          ServicId: 2,
          ServicText: "الخدمات البرمجية",
          ServicIcon: "mdi-blender-software",
          ServicColor: "blue--text text--darken-2",
        },
        {
          ServicId: 3,
          ServicText: "الخدمات العقارية",
          ServicIcon: "mdi-home-group",
          ServicColor: "",
        },
        // {
        //   ServicId: 3,
        //   ServicText: "خدمة توصيل",
        //   ServicIcon: "mdi-moped",
        //   ServicColor: "",
        // },
        // {
        //   ServicId: 5,
        //   ServicText: " شقق وفنادق",
        //   ServicIcon: "mdi-home-city-outline",
        //   ServicColor: "cyan--text text--accent-4",
        // },
        {
          ServicId: 6,
          ServicText: "  السفر والسياحة",
          ServicIcon: "mdi-plane-train",
          ServicColor: "deep-orange--text",
        },
        // {
        //   ServicId: 7,
        //   ServicText: "خدمة المركبات",
        //   ServicIcon: "mdi-car-key",
        //   ServicColor: "yellow--text text--darken-4",
        // },
        // {
        //   ServicId: 8,
        //   ServicText: "الصيانة",
        //   ServicIcon: "mdi-tools",
        //   ServicColor: "grey--text text--accent-3",
        // },
        // {
        //   ServicId: 9,
        //   ServicText: " خدمات اخرى",
        //   ServicIcon: "mdi-filter-variant",
        //   ServicColor: "amber--text text--accent-3",
        // },
      ],
      swiperOption: {
        initialSlide: 0,
        freeMode: false,
        effect: "cards",
        spaceBetween: 8,
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
            slidesPerView: 4,
            slidesPerGroup: 4,
          },
          250: {
            slidesPerView: 4,
            slidesPerGroup: 4,
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
  .ServiceCard {
    position: relative;
  }
  .icon {
    font-size: 25px;
    // background-color: #eee;
    padding: 8px;
    // width: 20px;
    // height: 20px;
    border-radius: 50% !important;
    color: #b2dfdb;
    position: relative;
    z-index: 2;
    box-shadow: 0px 0px 0px 3px $color-background !important;
    // border: 1px solid ;
    // margin-top: -10px !important;

    // box-shadow: 0px 0px 5px 0px $fontcolorlinks;
    @media (max-width: 750px) {
      font-size: 25px;
      padding: 6px;
    }
  }

  .swiper {
    height: 120px;
  }
  .swiperR {
    height: 300px;
    @media (max-width: 700px) {
      height: 270px;
    }
  }
  ::v-deep .swiper-container-horizontal > .swiper-pagination-progressbar {
    top: 95% !important;
    width: 50px;
    height: 5px;
    left: 50%;
    transform: translateX(-50%);
    border-radius: 10px;
    overflow: hidden;
    background-color: #eee;

    span.swiper-pagination-progressbar-fill {
      background-color: $color-2;
    }
  }

  .card-text {
    font-family: $fontfamliy3;
    letter-spacing: 0;
    font-size: 14px;
    font-weight: 600;
    color: $fontcolorlinks !important;
    height: 40px !important;

    @media (max-width: 600px) {
      font-size: 12px;
      height: 45px !important;
    }
  }
  .ser-text {
    font-family: $fontfamliy3;
    letter-spacing: 0;
    font-size: 14px;
    font-weight: 600;
    color: $fontcolorlinks !important;

    @media (max-width: 600px) {
      font-size: 13px;
    }
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
::v-deep .v-avatar.rounded-0 {
  @media (max-width: 600px) {
    height: 50px !important;
    min-width: 50px !important;
    width: 50px !important;
  }
}

</style>
