<template>
  <div class="Products">
    <TheNavBar />
    <v-container>
      <div class="hidden-sm-and-up">
        <FilterSearch />
        <v-row no-gutters>
          <v-col
            cols="6"
            md="3"
            sm="4"
            lg="2"
            xl="2"
            class="pa-1"
            v-for="Product in Products"
            :key="Product.id"
          >
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
              height="220px"
            >
              <v-img
                height="120"
                full-width
                :src="getimageUrl(Product.folder, Product.image)"
              ></v-img>
              <v-card-text
                class="d-inline-block card-text pb-0 pa-2 text-truncate"
              >
                {{ Product.name }} {{ Product.company }}
              </v-card-text>
              <strong class="red--text text--lighten-2 px-2 text-truncate">
                {{ Product.payment }}
                <small class="text-truncate">ريال</small>
              </strong>
              <v-spacer></v-spacer>
              <v-card-actions class="justify-space-between pt-1 pa-0">
                <div class="discount-tag">
                  <span>9%</span>
                </div>
                <p class="ma-0 sold-info px-2 text-truncate">
                  باع {{ Product.id }}
                </p>
              </v-card-actions>
            </v-card>
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
      <v-sheet class="transparent hidden-xs-only">
        <v-row no-gutters>
          <v-col cols="3" md="2" sm="3" lg="2">
            <FilterSearch />
          </v-col>
          <v-col cols="12" md="10" lg="10" sm="9">
            <v-row no-gutters>
              <v-col
                cols="6"
                md="3"
                sm="4"
                lg="2"
                xl="2"
                class="pa-1"
                v-for="Product in Products"
                :key="Product.id"
              >
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
                  height="220px"
                >
                  <v-img
                    height="120"
                    full-width
                    :src="getimageUrl(Product.folder, Product.image)"
                  ></v-img>
                  <v-card-text
                    class="d-inline-block card-text pb-0 pa-2 text-truncate"
                  >
                    {{ Product.name }} {{ Product.company }}
                  </v-card-text>
                  <strong class="red--text text--lighten-2 px-2 text-truncate">
                    {{ Product.payment }}
                    <small class="text-truncate">ريال</small>
                  </strong>
                  <v-spacer></v-spacer>
                  <v-card-actions class="justify-space-between pt-1 pa-0">
                    <div class="discount-tag">
                      <span>9%</span>
                    </div>
                    <p class="ma-0 sold-info px-2 text-truncate">
                      باع {{ Product.id }}
                    </p>
                  </v-card-actions>
                </v-card>
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
  color: $fontcolor !important;
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
</style>
