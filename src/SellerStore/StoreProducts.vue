<template>
  <div class="AboutStore">
    <v-btn-toggle dense v-model="text" tile color="primary" group>
      <v-menu
        v-model="menu"
        style="z-index: 16"
        bottom
        left
        offset-y
        open-on-hover
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            class="btn-categories"
            elevation="0"
            color="transparent"
            v-bind="attrs"
            v-on="on"
          >
            الفئات
            <v-icon
              size="22"
              v-text="menu ? 'mdi-menu-up' : 'mdi-menu-down'"
            ></v-icon>
          </v-btn>
        </template>

        <v-list class="mt-2">
          <v-list-item v-for="i in 5" :key="i">
            <v-list-item-title>{{ i }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
      <v-btn class="btn-categories" value="TopSales"> أعلى المبيعات </v-btn>
      <v-btn class="btn-categories" value="latest"> الأجدد </v-btn>
      <v-btn class="btn-categories" value="all"> الكل </v-btn>
    </v-btn-toggle>
    <v-row no-gutters>
      <v-col
        cols="6"
        md="2"
        sm="3"
        lg="2"
        class="pa-2"
        v-for="Product in Products"
        :key="Product.id"
      >
        <div style="position: relative">
          <h1 class="ribbon">متميز</h1>
          <v-card
            :to="{
              name: 'ShowTheProduct',
              params: {
                carName: Product.name,
                carShape: Product.Shape,
                carId: Product.id,
                Company: Product.folder,
              },
            }"
            min-height="220px"
            width="100%"
            style="overflow: hidden"
            flat
            tile
            color="transparent"
          >
            <div v-if="Product.discountPercent" class="best-price-tag">
              <small class="discountPercent">
                {{ Product.discountPercent }}-
              </small>
            </div>
            <v-img
              height="170"
              full-width
              :src="getimageUrl(Product.folder, Product.image)"
            ></v-img>
            <v-card-text
              class="d-inline-block card-text py-0 pa-2 text-truncate"
            >
              {{ Product.name }} {{ Product.company }}
            </v-card-text>
            <v-card-actions class="py-0 justify-space-between">
              <strong
                class="grey--text text--lighten-1 PriceBefore text-truncate"
              >
                {{ Product.payment }}
                <small class="text-truncate">ريال</small>
              </strong>
              <strong class="PriceAfter text-truncate">
                {{ Product.payment }}
                <small class="text-truncate">ريال</small>
              </strong>
            </v-card-actions>
            <v-card-actions class="py-1 justify-space-between">
              <p class="ma-0 sold-info px-2 text-truncate">
                <span>{{ Product.id }} </span>بيعت
              </p>
              <span class="card-text grey--text px-2">
                {{ Product.location }}
              </span>
            </v-card-actions>
          </v-card>
        </div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import Services from "../data-json/showroom.json";
import Products from "../data-json/All-Car.json";

export default {
  name: "ServicesPage",
  components: {},
  data() {
    return {
      Services,
      Products,
      model: null,
      menu: false,
      text: "all",
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
.AboutStore {
  //   padding: 20px 0;
  margin-bottom: 10px;
  background-color: $color-background !important;

  .titel {
    letter-spacing: 0 !important;
    font-size: 17px !important;
    font-weight: 500 !important;
    font-family: $fontfamliy3 !important;
    color: $fontcolor !important;
  }
  .btn-categories {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorlinks;
    font-size: 16px;
    @media (max-width: 600px) {
      font-size: 13px;
    }
  }
}
::v-deep .v-banner__wrapper {
  padding: 0 !important;
  border: 0 !important;
}
// Products
.sold-info {
  font-family: $fontfamliy3 !important;
  font-size: 13px !important;
  font-weight: 600 !important;
  color: $fontcolorlinks;
  span {
    color: $color-2 !important;
    margin-left: 5px;
    font-size: 14px !important;
    letter-spacing: 1.5px !important;
  }
}
.card-text {
  font-family: $fontfamliy3 !important;
  font-size: 13px;
}
.PriceBefore {
  font-size: 13px !important;
  text-decoration: line-through;
}
.PriceAfter {
  font-size: 14px !important;
  display: block;
  text-align: left;
  color: $color-2;
}
.best-price-tag {
  position: absolute;
  left: 4px;
  top: 0px;
  clip-path: polygon(
    50% 0%,
    100% 0,
    100% 35%,
    100% 70%,
    100% 100%,
    49% 70%,
    0 100%,
    0% 70%,
    0% 35%,
    0 0
  );

  background-color: $color-2;
  width: 35px;
  height: 40px;
  display: flex;
  justify-content: center;
  // transform: rotate(360deg);
  z-index: 5;
  border-radius: 0 !important;
}
.discountPercent {
  color: white !important;
  font-weight: 500;
  font-size: 13px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 10px;
} //
.ribbon {
  position: absolute;
  top: 3px;
  right: 0px;
  z-index: 15;
  padding: 0 5px;
  width: 50px;
  text-align: center;
  font-size: 11px;
  color: #ffffff;
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  border-radius: 5px 0px 0px 5px !important;
  background: $color-2;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.5);
}
.ribbon:before {
  content: "";
  position: absolute;
  display: block;
  width: 0.5em;
  height: 100%;
  padding: 0 0 20px 0px !important;
  top: 0;
  right: -0.51em;
  background: inherit;
  border-radius: 0px 5px 5px 0px !important;
}
// featured
.ribbon:after {
  position: absolute;
  content: "";
  display: block;
  width: 0.313em;
  height: 0.313em;
  background: rgba(0, 0, 0, 0.35);
  bottom: -0.313em;
  right: -0.3em;
  border-radius: 0px 5px 5px 0px !important;
  box-shadow: inset -1px 2px 2px rgba(0, 0, 0, 0.3);
}
::v-deep .v-banner__content {
  padding: 0 !important;
}
::v-deep
  .v-banner.hidden-md-and-up.v-sheet.theme--light.elevation-2.v-banner--is-mobile.v-banner--sticky {
  z-index: 18 !important;
}
</style>
