<template>
  <div class="Products">
    <TheNavBar />
    <v-container>
      <!-- fillter big screen from 600px and up -->
      <v-card flat class="grey lighten-2 hidden-xs-only">
        <v-card-actions class="pa-2">
          <v-select
            dense
            class="mx-1"
            hide-details
            flat
            :items="items"
            placeholder="ترتيب حسب المنطقة"
            solo
          ></v-select>
          <v-select
            dense
            class="mx-1"
            hide-details
            flat
            :items="items"
            placeholder="ترتيب حسب المنطقة"
            solo
          ></v-select>
          <v-select
            dense
            class="mx-1"
            hide-details
            flat
            :items="items"
            placeholder="ترتيب حسب المنطقة"
            solo
          ></v-select>
        </v-card-actions>
      </v-card>
      <!-- fillter small screen from 600px and down -->
      <div class="hidden-sm-and-up filtertion">
        <v-dialog
          no-click-animation
          v-model="filterdialog"
          persistent
          max-width="360"
        >
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              color="filtertion-btn"
              class="primary filtertion-btn"
              dark
              icon
              v-bind="attrs"
              v-on="on"
              elevation="8"
              width="52"
              height="52"
            >
              <v-icon>mdi-filter</v-icon>
            </v-btn>
          </template>
          <v-card class="grey lighten-2 pa-2">
            <v-select
              dense
              class="ma-2"
              hide-details
              flat
              :items="items"
              placeholder="ترتيب حسب المنطقة"
              solo
            ></v-select>
            <v-select
              dense
              class="ma-2"
              hide-details
              flat
              :items="items"
              placeholder="ترتيب حسب المنطقة"
              solo
            ></v-select>
            <v-select
              dense
              class="ma-2"
              hide-details
              flat
              :items="items"
              placeholder="ترتيب حسب المنطقة"
              solo
            ></v-select>
            <v-card-actions class="pa-0">
              <v-btn
                color="green "
                class="btn"
                text
                small
                @click="filterdialog = false"
              >
                عرض
              </v-btn>
              <v-spacer></v-spacer>
              <v-btn
                color="red darken-1 "
                class="btn"
                text
                small
                @click="filterdialog = false"
              >
                إلغاء
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </div>
      <v-sheet rounded class="grey lighten-2 pa-2 mt-3">
        <v-row no-gutters class="fill-height">
          <v-col
            cols="6"
            md="4"
            sm="6"
            lg="3"
            xl="1"
            class="pa-1"
            v-for="(Servic, i) in Services"
            :key="i"
          >
            <v-card flat to="/SellerStorePage" height="250px">
              <v-img
                class="mx-auto grey darken-3"
                aspect-ratio="2"
                contain
                :src="getimageUrl(Servic.folder, Servic.ShowroomImg)"
              ></v-img>
              <v-card-text class="card-text pa-2 text-truncate">
                {{ Servic.ShowroomName }}
              </v-card-text>
              <p class="ma-0 location px-2 text-truncate">
                {{ Servic.location }}
              </p>
              <v-card-title
                class="customer-rating-text pa-2 py-0 text-truncate"
              >
                تقييمات العملاء :
                <v-spacer></v-spacer>
                <v-rating
                  background-color="warning lighten-1"
                  color="warning"
                  dense
                  half-increments
                  hover
                  length="5"
                  readonly
                  size="16"
                  value="3.5"
                ></v-rating>
              </v-card-title>
            </v-card>
          </v-col>
          <v-col cols="12" class="mt-2">
            <v-card-actions class="justify-center">
              <v-btn elevation="0" width="190" class="seeMoreBtn">
                المزيد
                <v-icon right size="16">mdi-dots-horizontal</v-icon>
              </v-btn>
            </v-card-actions>
          </v-col>
        </v-row>
        <!-- <v-col cols="12">
          <v-card-actions class="justify-center">
            <v-btn outlined elevation="0" width="190" class="seeMoreBtn">
              المزيد
              <v-icon right>mdi-dots-horizontal</v-icon>
            </v-btn>
          </v-card-actions>
        </v-col> -->
      </v-sheet>
    </v-container>
  </div>
</template>

<script>
import Services from "../data-json/showroom.json";
import TheNavBar from "../NavBar/TheNavBar.vue";
export default {
  name: "ServicesPage",
  components: { TheNavBar },
  data() {
    return {
      Services,
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
  // computed: {
  //   getCarInfo() {
  //     let GetShowroomfeatured = [];
  //     for (let i = 0; i < this.featuredshowrooms.length; i++) {
  //       if (this.featuredshowrooms[i].featured == true) {
  //         GetShowroomfeatured.push(this.featuredshowrooms[i]);
  //       }
  //     }
  //     return GetShowroomfeatured;
  //   },
  // },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.Products {
  width: 100%;
  min-height: 70vh;
  background-color: $color-background;
  font-family: $fontfamliy;
  .location {
    font-size: 14px !important;
    font-weight: 500 !important;
    color: $fontcolorlinks !important;
  }
  .seeMoreBtn {
    letter-spacing: 0 !important;
    font-size: 16px;
    font-family: $fontfamliy2;
    color: $color-2;
  }
}
.card-text {
  font-family: $fontfamliy3 !important;
  color: $fontcolor !important;
}
.customer-rating-text {
  font-family: $fontfamliy3;
  font-size: 14px;
  color: $fontcolorlinks !important;
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
  a {
    font-size: 13px;
    text-decoration: none !important;
    font-weight: 600 !important;
  }
}
.container {
  @media (max-width: 600px) {
    padding: 0 !important;
  }
}
::v-deep .v-dialog.v-dialog--active.v-dialog--persistent {
  margin: 5px;
}
::v-deep .v-select__selection.v-select__selection--comma {
  font-family: $fontfamliy3;
  font-size: 14px;
  letter-spacing: 0;
}
::v-deep .v-list-item__title {
  font-family: $fontfamliy3;
  font-size: 14px !important;
  letter-spacing: 0;
}
::v-deep input {
  font-family: $fontfamliy3;
  font-size: 14px !important;
  letter-spacing: 0;
}
.filtertion {
  position: fixed;
  z-index: 6;
  left: 8px;
  bottom: 46px;
}
.filtertion-btn {
  letter-spacing: 0 !important;
  font-size: 18px;
  font-family: $fontfamliy3;
  transform: scale(0.8);
}
.btn {
  letter-spacing: 0 !important;
  font-size: 18px;
  font-family: $fontfamliy3;
}
</style>
