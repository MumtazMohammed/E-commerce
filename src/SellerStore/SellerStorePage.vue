<template>
  <div class="Sellerstore">
    <v-app-bar height="70" app color="grey lighten-2" elevate-on-scroll fixed>
      <v-toolbar-title>
        <v-img
          class="hidden-sm-and-down"
          contain
          width="170"
          height="50"
          src="../assets/outsrc/logo.png"
        ></v-img>
      </v-toolbar-title>
      <v-spacer class="hidden-sm-and-down"></v-spacer>
      <v-col cols="12" md="8" class="pa-0">
        <v-card flat style="overflow: hidden" class="d-flex align-center">
          <v-btn
            style="transition: all 0.2s 0s linear"
            class="btn"
            tile
            elevation="0"
            height="38px"
          >
            <v-icon
              :size="first.length > 0 ? '23' : '20'"
              color="white"
              first.length
            >
              mdi-magnify
            </v-icon>
          </v-btn>
          <v-text-field
            flat
            dense
            hide-details
            v-model="first"
            label="ابحث في هذا المتجر"
            solo
          ></v-text-field>
        </v-card>
      </v-col>
      <v-spacer class="hidden-sm-and-down"></v-spacer>

      <!-- cart shopping  -->
      <v-badge
        bordered
        offset-x="45"
        offset-y="12"
        overlap
        content="5"
        class="mx-2 hidden-sm-and-down"
      >
        <v-btn
          :to="{
            name: 'TheClientCartPage',
            params: { SavedAd: 'سلة التسوق ' },
          }"
          depressed
          class="btn-noti-cart"
          icon
          width="38"
          height="38"
        >
          <v-icon class="btn-noti-cart-icon">mdi-cart-outline</v-icon>
        </v-btn>
      </v-badge>
      <!-- notification btn -->
      <v-badge
        bordered
        offset-x="45"
        offset-y="12"
        overlap
        content="1"
        class="mx-2 hidden-sm-and-down"
      >
        <v-btn width="38" height="38" depressed class="btn-noti-cart" icon>
          <v-icon class="btn-noti-cart-icon">mdi-bell-outline</v-icon>
        </v-btn>
      </v-badge>
    </v-app-bar>
    <v-sheet style="margin-top: 70px">
      <v-container class="container-info">
        <div class="">
          <seller-info />
        </div>
      </v-container>
      <v-container class="py-0">
        <div class="mt-2">
          <store-voucher />
        </div>
        <div class="mt-2">
          <about-store />
        </div>
        <div class="mt-2">
          <store-products />
        </div>
      </v-container>
    </v-sheet>
  </div>
</template>

<script>
import Services from "../data-json/showroom.json";
import SellerInfo from "./SellerInfo.vue";
import StoreVoucher from "./StoreVoucher.vue";
import AboutStore from "./AboutStore.vue";
import StoreProducts from "./StoreProducts.vue";
export default {
  name: "ServicesPage",
  components: { SellerInfo, StoreVoucher, AboutStore, StoreProducts },
  data() {
    return {
      Services,
      first: "",
      filterdialog: null,
      items: ["مقديشو", "كزبرا", "صلصة", "ثوم"],
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.Sellerstore {
  width: 100%;
  min-height: 100vh;
  background-color: $color-background;
}

.btn {
  background-color: $color-2 !important;
}
.btn-noti-cart {
  color: $color-2 !important;
  background-color: #eee;
  @media (max-width: 600px) {
    border: none !important;
    color: $color-2 !important;
  }
}
::v-deep .theme--light.v-badge .v-badge__badge:after {
  border-width: 0;
}
::v-deep span.v-badge__badge {
  background-color: #eee !important;
  color: $color-2 !important;
  font-weight: 500;
  @media (max-width: 600px) {
    inset: auto calc(100% - 45px) calc(100% - 10px) auto !important;
  }
}
.btn-noti-cart-icon {
  font-size: 20px !important;
}
::v-deep
  header.v-sheet.theme--light.v-toolbar.v-app-bar.v-app-bar--elevate-on-scroll.v-app-bar--fixed.v-app-bar--is-scrolled.grey {
  z-index: 20;
}
::v-deep .container-info {
  @media (max-width: 600px) {
  }
}
::v-deep label.v-label.theme--light {
  font-family: $fontfamliy3;
  font-size: 14px;
  color: #bdbdbd;
}
</style>
