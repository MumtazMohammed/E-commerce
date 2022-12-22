<template>
  <div class="Products">
    <TheNavBar />
    <v-container>
      <div class="hidden-md-and-up">
        <FilterSearch />
        <v-row no-gutters>
          <v-col
            cols="6"
            md="2"
            sm="3"
            lg="2"
            xl="2"
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
                width="100%"
                min-height="220"
                tile
                flat
                color="transparent"
                style="overflow: hidden"
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
          <!-- <v-col cols="12" class="mt-2">
                <v-card-actions class="justify-center">
                  <v-btn elevation="0" width="190" class="seeMoreBtn">
                    المزيد
                    <v-icon right size="16">mdi-dots-horizontal</v-icon>
                  </v-btn>
                </v-card-actions>
              </v-col> -->
        </v-row>
      </div>
      <v-sheet class="transparent hidden-sm-and-down">
        <v-row no-gutters>
          <v-col cols="3" md="2" sm="3" lg="2">
            <FilterSearch />
          </v-col>
          <v-col cols="12" md="10" lg="10" sm="10">
            <v-row no-gutters>
              <v-col
                cols="6"
                md="3"
                sm="4"
                lg="3"
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
                    width="100%"
                    min-height="220"
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
              <!-- <v-col cols="12" class="mt-2">
                <v-card-actions class="justify-center">
                  <v-btn elevation="0" width="190" class="seeMoreBtn">
                    المزيد
                    <v-icon right size="16">mdi-dots-horizontal</v-icon>
                  </v-btn>
                </v-card-actions>
              </v-col> -->
            </v-row>
          </v-col>
        </v-row>
      </v-sheet>
    </v-container>
    <FixedBottomNav class="hidden-sm-and-up" />
  </div>
</template>

<script>
import TheNavBar from "../NavBar/TheNavBar.vue";
import FixedBottomNav from "../NavBar/FixedBottomNav.vue";
import Products from "../data-json/All-Car.json";
import FilterSearch from "./FilterSearch.vue";
export default {
  name: "Products",
  components: { FixedBottomNav, TheNavBar, FilterSearch },
  data() {
    return {
      Products,
      items: ["Foo", "Bar", "Fizz", "Buzz"],
      filterdialog: null,
      admins: [
        ["Management", "mdi-account-multiple-outline"],
        ["Settings", "mdi-cog-outline"],
      ],
      cruds: [
        ["Create", "mdi-plus-outline"],
        ["Read", "mdi-file-outline"],
        ["Update", "mdi-update"],
        ["Delete", "mdi-delete"],
      ],
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
.Products {
  width: 100%;
  min-height: 70vh;
  background-color: $color-background;
  @media (max-width: 600px) {
    margin-bottom: 50px;
  }
  .discount-tag {
    width: 45px;
    height: 20px;
    clip-path: polygon(25% 0%, 100% 0%, 100% 100%, 25% 100%, 10% 50%);
    background-color: $color-2;
    color: #fff !important;
    font-size: 15px;
    font-weight: 500;
    justify-content: start;
    padding-right: 1px;
  }
  .sold-info {
    font-size: 13px !important;
    font-weight: 500 !important;
    color: grey !important;
  }
  // .seeMoreBtn {
  //   letter-spacing: 0 !important;
  //   font-size: 16px;
  //   font-family: $fontfamliy3;
  //   color: $color-2;
  // }
}
.card-text {
  font-family: $fontfamliy3 !important;
  color: $fontcolor;
  letter-spacing: 0 !important;
  font-size: 13px !important;
}
.tital {
  font-family: $fontfamliy3;
  font-size: 16px;
  color: $fontcolorlinks;
  letter-spacing: 0px !important;
  @media (max-width: 470px) {
    font-size: 14px;
  }
  @media (max-width: 350px) {
    font-size: 13px;
  }
  strong {
    color: $color-2;
  }
}

::v-deep .overflow-y-auto.transparent.v-sheet.theme--light::-webkit-scrollbar {
  display: none;
}
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
  color: $fontcolor !important;
  font-size: 13px !important;
}
.PriceBefore {
  font-size: 13px !important;
  text-decoration: line-through;
}
.PriceAfter {
  font-size: 14px !important;
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
}
.seeMoreBtn {
  letter-spacing: 0 !important;
  font-size: 16px;
  font-family: $fontfamliy3;
  color: $color-2;
  background-color: #ffffff !important;
}

//
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
@media (max-width: 1260px) {
  .container {
    max-width: 100% !important;
  }
}
@media (max-width: 600px) {
  .container {
    padding: 0;
  }
}
</style>
