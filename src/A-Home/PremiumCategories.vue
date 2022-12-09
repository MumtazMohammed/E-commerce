<template>
  <div class="SpicalShowRoom">
    <v-container class="py-0">
      <v-col>
        <div class="mb-2 tital">
          الشركات
          <strong class="mx-1">التجارية</strong>
        </div>
      </v-col>
      <v-row no-gutters class="">
        <v-col class="pa-2" v-for="i in 6" :key="i">
          <v-card outlined height="" to="/contact">
            <v-card-actions class="justify-center pa-0">
              <v-img
                height="125"
                max-width="125"
                src="../assets/outsrc/adidas-logo.png"
                alt="../assets/outsrc/adidas-logo.png"
              ></v-img>
            </v-card-actions>
            <v-divider></v-divider>
            <p class="ma-0 my-2">نايك</p>
          </v-card>
        </v-col>
      </v-row>
      <!-- small screen view -->
    </v-container>
  </div>
</template>

<script>
import featuredshowrooms from "../data-json/showroom.json";

export default {
  name: "SpicalShowRoom",
  components: {},

  data() {
    return {
      Tital: "المعارض المتميزة",
      featuredshowrooms,
      swiperOptionSmall: {
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
          clickable: false,
        },

        breakpoints: {
          960: {
            slidesPerView: 3,
          },
          789: {
            slidesPerView: 3,
          },
          788: {
            slidesPerView: 2,
          },
          640: {
            slidesPerView: 2,
          },
          472: {
            slidesPerView: 1,
          },
          471: {
            slidesPerView: 1,
          },
          470: {
            slidesPerView: 1,
          },
          250: {
            slidesPerView: 1,
          },
        },
      },
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
          960: {
            slidesPerView: 4,
          },
          640: {
            slidesPerView: 3,
            slidesPerGroup: 3,
          },
          472: {
            slidesPerView: 2,
          },
          471: {
            slidesPerView: 2,
          },
          470: {
            slidesPerView: 2,
          },
          250: {
            slidesPerView: 1,
          },
        },
      },
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
  computed: {
    getCarInfo() {
      let GetShowroomfeatured = [];
      for (let i = 0; i < this.featuredshowrooms.length; i++) {
        if (this.featuredshowrooms[i].featured == true) {
          GetShowroomfeatured.push(this.featuredshowrooms[i]);
        }
      }
      return GetShowroomfeatured;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.SpicalShowRoom {
  width: 100%;
  min-height: 40vh;
  background-color: $color-background;
  .tital {
    position: relative;
    text-align: center;
    font-family: $fontfamliy3;
    font-size: 20px;
    color: $fontcolorlinks;
    font-weight: 600;
    pointer-events: none;
    @media (max-width: 400px) {
      font-size: 16px;
    }
    strong {
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
      width: 25%;
    }
    @media (max-width: 360px) {
      width: 20%;
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
      width: 25%;
    }
    @media (max-width: 360px) {
      width: 20%;
    }
  }
}

p {
  // margin: 0 !important;
  text-align: center !important;
  font-family: $fontfamliy2;
  letter-spacing: 0 !important;
  color: $fontcolorlinks;
}
</style>
