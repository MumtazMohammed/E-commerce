<template>
  <v-main>
    <NavBar />
    <div class="car-reviw">
      <v-container class="pa-0">
        <v-row no-gutters class="mt-1">
          <v-col cols="12">
            <ProductImages />
          </v-col>
          <v-col cols="12">
            <TheSellerStoreInformation />
          </v-col>
          <v-col cols="12">
            <AdvertisementTow />
          </v-col>
          <v-col cols="12"><ProductRatings /> </v-col>
          <v-col cols="12" class="pa-0">
            <SameWonerProducts />
          </v-col>
          <v-col cols="12" class="pa-0">
            <YouMightLikeIt />
          </v-col>
        </v-row>
      </v-container>
    </div>
  </v-main>
</template>
<script>
import NavBar from "@/NavBar/TheNavBar.vue";
// import SearchBar from "../Search/SearchBar.vue";
import CarData from "@/data-json/All-Car.json";
import ProductImages from "@/ProductsDetail/ProductImages.vue";
import TheSellerStoreInformation from "@/ProductsDetail/TheSellerStoreInformation.vue";
import ProductRatings from "@/ProductsDetail/ProductRatings.vue";
import SameWonerProducts from "@/ProductsDetail/SameWonerProducts.vue";
import YouMightLikeIt from "@/A-Home/YouMightLikeIt.vue";
import AdvertisementTow from "@/Advertisement/AdvertisementTow.vue";

export default {
  name: "ShowTheProductsInfo",
  components: {
    NavBar,
    ProductImages,
    TheSellerStoreInformation,
    ProductRatings,
    YouMightLikeIt,
    SameWonerProducts,
    AdvertisementTow,
  },
  data() {
    return {
      dialog: false,
      GetCarData: CarData,
      carName: this.$route.params.carName,
      carId: this.$route.params.carId,
      CarShape: this.$route.params.CarShape,
      Company: this.$route.params.Company,
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
.car-reviw {
  width: 100%;
  height: auto;
  position: relative;
  background-color: $color-background;
}
.container {
  @media (max-width: 1265px) {
    max-width: 100%;
  }
  @media (max-width: 600px) {
    padding-top: 0px;
  }
}
</style>
