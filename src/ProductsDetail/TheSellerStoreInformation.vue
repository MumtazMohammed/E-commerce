<template>
  <div class="car-info my-4">
    <div class="store-col">
      <v-card flat class="store-card store-col" width="100%">
        <v-card-actions class="flex-wrap">
          <v-avatar size="70px" color="transparent">
            <img
              src="../assets/showroom/orignal-1615322218-744.png"
              alt="alt"
            />
          </v-avatar>
          <div class="mr-3 store">
            <p class="text-truncate store-name">تفاصيل</p>
            <v-btn to="/SellerStorePage" outlined class="owner-btns">
              رؤية المتجر
            </v-btn>
            <!-- <v-btn outlined class="owner-btns mr-1">
                <v-icon left>mdi-chat-processing-outline</v-icon>
                مراسلة
              </v-btn> -->
          </div>
          <div class="store">
            <span class="text-truncate d-inline-block store-name">تفاصيل </span>

            <span class="text-truncate d-inline-block store-name">تفاصيل </span>

            <span class="text-truncate d-inline-block store-name">تفاصيل </span>

            <!-- <v-btn outlined class="owner-btns mr-1">
                <v-icon left>mdi-chat-processing-outline</v-icon>
                مراسلة
              </v-btn> -->
          </div>
        </v-card-actions>
      </v-card>
    </div>
    <v-card outlined flat class="detail-card pa-1 mt-3">
      <p class="tital pa-2">تفاصيل المنتج</p>
      <v-card-text
        class="pa-2 text"
        :style="SeeMore ? 'height: auto !important' : ''"
      >
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
      <div
        :class="SeeMore ? 'see-less' : 'see-more'"
        v-text="SeeMore ? 'أقراء أقل' : 'أقراء المزيد'"
        @click="SeeMore = !SeeMore"
      ></div>
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
  font-size: 17px;
  color: $fontcolor;
  font-weight: 500;
  pointer-events: none;
  @media (max-width: 400px) {
    font-size: 17px;
  }
  // store {
  //   color: $color-2;
  // }
}

.store-col {
  @media (max-width: 650px) {
    padding-left: 0px !important ;
    padding-right: 0px !important ;
  }
  .store-card {
    @media (max-width: 650px) {
      border-radius: 0px !important;
    }
    .store {
      width: 40%;
      flex-wrap: wrap;

      @media (max-width: 550px) {
        width: calc(100% - 78px);
        display: flex;
        justify-content: space-between;
        align-items: center;
      }
      @media (max-width: 500px) {
        width: calc(100% - 57px);
      }
      .store-name {
        letter-spacing: 0 !important;
        font-family: $fontfamliy;
        text-align: justify;
        pointer-events: none;

        margin: 0 5px 8px 0px !important;
        @media (max-width: 550px) {
          margin: 0 5px 0px 0px !important;
        }
      }
      .owner-btns {
        letter-spacing: 0 !important;
        font-family: $fontfamliy;
        color: $fontcolorlinks !important;
        @media (max-width: 450px) {
          padding: 0 5px !important;
        }
      }
    }
  }
}
.store:last-child {
  display: flex;
  justify-content: space-around;
  @media (max-width: 550px) {
    width: 100% !important;
    margin-top: 10px;
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
    font-size: 13px;
    font-weight: 500;
    line-height: 1.5;
    height: 70px;
    overflow: hidden;
    pointer-events: none;
    @media (max-width: 400px) {
      font-size: 13px;
    }
  }
  .see-more {
    // position: absolute;
    position: relative;
    z-index: 5;
    width: 100%;
    box-shadow: 0px -6px 18px 9px white;
    text-align: center;
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    color: $fontcolorlinks;
    cursor: pointer;
    font-size: 14px;
  }
  .see-less {
    text-align: center;
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    color: $fontcolorlinks;
    cursor: pointer;
    font-size: 14px;
  }
}
</style>
