<template>
  <div class="SpicalShowRoom py-2">
    <v-container class="pa-0">
      <v-col class="pa-0">
        <div class="mb-2 tital">
          الشركات
          <strong class="mx-1">التجارية</strong>
        </div>
      </v-col>

      <v-row no-gutters class="">
        <v-col
          md="2"
          sm="4"
          lg="2"
          cols="6"
          class="pa-1"
          v-for="i in 6"
          :key="i"
        >
          <v-card class="mx-auto" color="grey lighten-4">
            <v-img
              height="150"
              contain
              class="white"
              src="../assets/outsrc/adidas-logo.png"
            >
            </v-img>
            <v-card-text class="pt-6" style="position: relative">
              <v-btn
                absolute
                color="#fc624d"
                class="white--text"
                fab
                left
                small
                top
                to="/SellerStorePage"
              >
                <v-icon>mdi-cart</v-icon>
              </v-btn>

              <v-card-text class="pa-0 brand"> أديداس </v-card-text>
              <!-- <div class="font-weight-light text-h6 mb-2">
                Our Vintage kitchen utensils delight any chef.<br />
                Made of bamboo by hand
              </div> -->
            </v-card-text>
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
    @media (max-width: 600px) {
      font-size: 16px;
    }
    @media (max-width: 350px) {
      font-size: 14px;
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

.brand {
  font-size: 18px;
  text-align: center !important;
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  font-weight: 600 !important;
  color: $color-2;
  @media (max-width: 600px) {
    font-size: 16px;
  }
}
::v-deep .v-image.v-responsive.theme--light {
  @media (max-width: 600px) {
    height: 100px !important;
  }
}
.v-card--reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: 0.5;
  position: absolute;
  width: 100%;
}
</style>
