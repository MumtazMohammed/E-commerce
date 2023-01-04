<template>
  <div class="car-info my-4">
    <div class="store-col ">
      <v-card tile flat class="store-card pa-2" width="100%">
        <v-card-actions class="flex-wrap pa-0">
          <v-avatar size="65px" rounded color="transparent">
            <img
              src="../assets/showroom/orignal-1615322218-744.png"
              alt="alt"
            />
          </v-avatar>

          <div class="store mr-3">
            <span class="text-truncate store-name">تفاصيل </span>
          </div>
          <v-spacer></v-spacer>
          <v-btn to="/SellerStorePage" small elevation="0" class="owner-btns">
            رؤية المتجر
          </v-btn>
        </v-card-actions>
      </v-card>
    </div>
    <v-card tile flat class="detail-card pa-1 mt-3">
      <p class="tital pa-2">تفاصيل المنتج</p>
      <v-card-text class="pa-2 text">
        الشكل والمبنى، من المهم أن يكون الموقع جاذبا من الناحية البصرية فهو
        يساعد المتصفح على فهم المحتوى أكثر وبالإضافة إلى الألوان التي ستجعل
        موقعك ذا إحساس عالي. التنوين، وهو على ثلاث أشكال: تنوين ضم وتنوين فتح
        وتنوين كسر هذا نص عشوائي الشكل الشكل والمبنى، من المهم أن يكون الموقع
        جاذبا من الناحية البصرية فهو يساعد الشكل والمبنى، من المهم أن يكون
        الموقع جاذبا من الناحية البصرية فهو يساعد المتصفح على فهم المحتوى أكثر
        وبالإضافة إلى الألوان التي ستجعل موقعك ذا إحساس عالي. التنوين، وهو على
        ثلاث أشكال: تنوين ضم وتنوين فتح وتنوين كسر هذا نص عشوائي الشكل الشكل
        والمبنى، من المهم أن يكون الموقع جاذبا من الناحية البصرية فهو يساعد
        <br />
        <br />
        <br />
        المتصفح على فهم المحتوى أكثر وبالإضافة إلى الألوان التي ستجعل موقعك ذا
        إحساس عالي. التنوين، وهو على ثلاث أشكال: تنوين ضم وتنوين فتح وتنوين كسر
        هذا نص عشوائي الشكل
      </v-card-text>
    </v-card>
    <!-- card discrption  -->
  </div>
</template>
<script>
import CarData from "../data-json/All-Car.json";

export default {
  name: "CarDetails",
  components: {},
  data() {
    return {
      SeeMore: null,
      GetCarData: CarData,
      carName: this.$route.params.carName,
      carId: this.$route.params.carId,
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
  // this computed to call the item by it info
  computed: {
    getCarInfo() {
      let Carinformation = "";
      for (let i = 0; i < this.GetCarData.length; i++) {
        if (this.GetCarData[i].id == this.carId) {
          Carinformation = this.GetCarData[i];
          break;
        }
      }
      return Carinformation;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.tital {
  position: relative;
  // text-align: center;
  font-family: $fontfamliy3;
  font-size: 16px;
  color: fontcolorlinks !important;
  font-weight: 600;
  pointer-events: none;
  @media (max-width: 400px) {
    font-size: 14px;
  }
  // store {
  //   color: $color-2;
  // }
}

.store-col {
  .store-card {
    overflow: hidden;
    .store {
      flex-wrap: wrap;
      .store-name {
        letter-spacing: 0 !important;
        font-family: $fontfamliy3;
        pointer-events: none;
        font-size: 16px !important;
        @media (max-width: 600px) {
          font-size: 13px !important;
          font-weight: 600;
        }
      }
    }
  }
}
.owner-btns {
  letter-spacing: 0 !important;
  font-family: $fontfamliy3;
  color: $fontcolorlinks !important;
  font-size: 16px !important;
  padding: 10px 15px !important;
  @media (max-width: 600px) {
    font-size: 14px !important;
  }
}

::v-deep .v-avatar.transparent {
  @media (max-width: 600px) {
    height: 50px !important;
    min-width: 50px !important;
    width: 50px !important;
  }
  @media (max-width: 500px) {
    height: 40px !important;
    min-width: 40px !important;
    width: 40px !important;
  }
}

.detail-card {
  overflow: hidden;
  .text {
    position: relative;
    font-family: $fontfamliy3;
    font-size: 14px;
    font-weight: 500;
    line-height: 1.6;
    overflow: hidden;
    pointer-events: none;
    @media (max-width: 400px) {
      font-size: 13px;
    }
  }
}
</style>
