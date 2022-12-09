<template>
  <!-- this component will be under the image  -->
  <div class="ContactSeller">
    <v-card-actions class="py-0 pt-1">
      <ShareSaveReport />
      <v-spacer></v-spacer>
      <div class="discount-tag ml-1">
        <span>متميز</span>
      </div>
      <div class="discount-tag">
        <span>9%</span>
        <span>خصم</span>
      </div>
    </v-card-actions>

    <!-- product name  -->
    <v-col cols="12" class="py-1">
      <p class="ProductName d-inline-block text-truncate ma-0">
        {{ getCarInfo.company }} {{ getCarInfo.name }}
        {{ getCarInfo.modle }}
      </p>
    </v-col>
    <!-- rating and sales Info   -->
    <v-card flat color="transparent">
      <v-card-actions class="py-0">
        <p class="ma-0">التقيمات</p>
        <span class="grey--text number text--darken-1 mr-1"> 9 </span>
        <v-divider vertical class="mx-2"></v-divider>
        <v-rating
          v-model="rating"
          half-increments
          background-color="orange"
          color="orange"
          small
          readonly
        ></v-rating>
        <span class="grey--text number text--darken-1 mr-1">
          {{ rating }}
        </span>
        <v-divider vertical class="mx-2"></v-divider>
        <p class="ma-0">المبيعات</p>
        <span class="grey--text number text--darken-1 mr-1"> 33 </span>
      </v-card-actions>
    </v-card>
    <!-- Price Info   -->
    <v-card-actions>
      <p class="ma-0 if-discount grey--text text--lighten-1">
        {{ getCarInfo.payment }}
        <span> ريال </span>
      </p>
      <p class="ma-0 mr-2 price red--text">
        {{ getCarInfo.payment }}
        <span> ريال </span>
      </p>
      <v-spacer></v-spacer>
    </v-card-actions>
    <v-menu max-width="600" open-on-hover bottom left>
      <template v-slot:activator="{ on, attrs }">
        <v-card-actions v-bind="attrs" v-on="on">
          <span class="see-more-coupons">القسائم</span>
          <v-sheet class="px-2 d-flex" width="100%">
            <span v-for="i in 3" :key="i" class="coupons">
              خصم
              <span class="mx-1">20%</span></span
            >
            <v-spacer></v-spacer>
            <span style="font-size: 13px" class="see-more-coupons"
              >رؤية الكل</span
            >
          </v-sheet>
        </v-card-actions>
      </template>
      <v-sheet
        style="overflow-y: scroll"
        height="300"
        class="pa-2 StoreVoucher"
      >
        <v-card-title class="titel py-2"> قسائم المتجر </v-card-title>
        <v-divider></v-divider>
        <v-row no-gutters class="mt-2">
          <v-col class="pa-1" cols="6" v-for="i in 5" :key="i">
            <v-card
              flat
              style="border: 2px dashed #ffd54f !important"
              color="amber lighten-5"
              class=""
            >
              <v-row no-gutters>
                <v-col>
                  <v-card-subtitle class="text py-0 px-1">
                    خصم <span class="mx-1"><span>20</span>%</span>
                  </v-card-subtitle>
                  <v-card-text class="py-0 px-1 text">
                    أنفق
                    <span class="mx-1">
                      52<v-icon size="17">mdi-currency-rial</v-icon>
                    </span>
                    كحد أدنى
                  </v-card-text>
                  <v-card-text class="py-0 px-1 mb-1 text">
                    متاح حتى
                    <span>10/2/2020</span>
                  </v-card-text>
                </v-col>
                <v-col style="margin: auto 0; text-align: center" cols="3">
                  <v-btn
                    small
                    dark
                    class="deep-orange btn lighten-1"
                    elevation="0"
                  >
                    أخذ
                  </v-btn>
                </v-col>
              </v-row>
            </v-card>
          </v-col>
        </v-row>
      </v-sheet>
    </v-menu>
  </div>
</template>
<script>
import CarData from "../data-json/All-Car.json";
import ShareSaveReport from "./ShareSaveReport.vue";
export default {
  name: "productInformation",
  components: { ShareSaveReport },
  data() {
    return {
      rating: 4.5,
      GetCarData: CarData,
      carName: this.$route.params.carName,
      carId: this.$route.params.carId,
      ShowPriceOption: true,
      ShowContac: false,
    };
  },
  // this is help full to call the image inside folder and inject to the src
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
.ProductName {
  font-family: $fontfamliy3 !important;
  color: $fontcolor !important;
  font-weight: 500;
  letter-spacing: 0 !important;
  font-size: 23px !important;
  width: 100%;
  @media (max-width: 600px) {
    font-size: 19px !important;
  }
  @media (max-width: 400px) {
    font-size: 16px !important;
  }
}
.price {
  font-size: 18px;
  @media (max-width: 500px) {
    font-size: 18px !important;
  }
  @media (max-width: 350px) {
    font-size: 16px !important;
  }
}
.if-discount {
  font-size: 16px;
  text-decoration: line-through;
  font-weight: 500 !important;
  font-family: $fontfamliy3 !important;
  @media (max-width: 500px) {
    font-size: 14px;
  }
}
p {
  font-family: $fontfamliy3 !important;
  font-weight: 500;
  font-size: 14px;
  @media (max-width: 600px) {
    font-size: 13px !important;
  }
  @media (max-width: 400px) {
    font-size: 12px !important;
  }
}
.number {
  border-bottom: 1.5px solid rgba(128, 128, 128, 0.718);
  @media (max-width: 600px) {
    font-size: 14px !important;
  }
  @media (max-width: 400px) {
    font-size: 12px !important;
  }
}
::v-deep
  button.v-icon.notranslate.v-icon--link.material-icons.theme--light.orange--text {
  font-size: 17px !important;
  padding: 1px !important;
}
.discount-tag {
  width: 80px;
  display: block;
  height: 25px;
  background-color: $color-2;
  color: #fff !important;
  font-size: 14px;
  font-weight: 500;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 2px;
  @media (max-width: 500px) {
    font-size: 13px;
  }
}
.discount-tag span:last-child {
  font-family: $fontfamliy3 !important;
  margin-right: 3px;
  color: #fff !important;
}
::v-deep ::v-deep .theme--light.v-btn:before {
  background-color: rgba(255, 255, 255, 0);
  transition: all 0.3s 0s ease;
}

::v-deep .theme--light.v-btn:hover:before {
  opacity: 0;
}
// coupons
.coupons {
  background-color: #ffecb3;
  font-family: $fontfamliy3 !important;
  padding: 0px 5px;
  margin: 0 3px;
  font-size: 14px;
  color: #e65100b3;
  border-radius: 3px;
  @media (max-width: 600px) {
    font-size: 12px;
  }
}
.see-more-coupons {
  font-family: $fontfamliy3 !important;
  color: $fontcolorlinks;
  font-size: 14px;
  @media (max-width: 600px) {
    font-size: 13px;
  }
}
// Voucher
.StoreVoucher {
  background-color: $color-background;
  .titel {
    letter-spacing: 0 !important;
    font-size: 17px !important;
    font-weight: 500 !important;
    font-family: $fontfamliy3 !important;
    color: $fontcolor !important;
  }
  .text {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorlinks !important;
    font-size: 13px !important;
  }
  .btn {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: #fff !important;
    font-size: 14px !important;
    font-weight: 600 !important;
    padding: 0 6px !important ;
    height: 25px !important;
    min-width: 37px !important;
    @media (max-width: 600px) {
      font-size: 13px !important;
    }
  }
}
::v-deep.v-menu__content.theme--light.menuable__content__active {
  @media (max-width: 600px) {
    left: 0 !important;
  }
}
</style>
