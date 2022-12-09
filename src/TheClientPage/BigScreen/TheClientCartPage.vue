<template>
  <div class="TheClientCartPage">
    <v-container>
      <v-card-title class="pa-0 cart-title">
        <v-icon right class="link-icon"> mdi-cart-plus </v-icon>
        سلة التسوق
      </v-card-title>
      <v-sheet height="600" class="overflow-y-auto pt-1">
        <v-row no-gutters class="">
          <v-col cols="8">
            <v-row no-gutters>
              <v-col class="mt-1" cols="12" v-for="i in 6" :key="i">
                <v-sheet outlined class="pa-1 grey lighten-4">
                  <v-card-actions>
                    <v-checkbox
                      hide-details
                      value="1"
                      class="ma-0 pa-0"
                      v-model="checkbox"
                    ></v-checkbox>
                    <v-card-text class="pa-1 store-name">
                      <v-icon right>mdi-store-outline </v-icon>
                      وقت العطور
                    </v-card-text>

                    <v-btn icon>
                      <v-icon class="chat-icon" size="20">mdi-message </v-icon>
                    </v-btn>
                  </v-card-actions>
                  <v-divider class="my-1 mb-3"></v-divider>
                  <v-card flat>
                    <v-card-actions class="justify-start align-start pa-0">
                      <v-avatar class="avatar" rounded size="80" color="#fff">
                        <v-img
                          src="@/assets/Mazda/mazda1.jpg"
                          alt="@/assets/Hyundai/image2.jpg"
                        ></v-img>
                      </v-avatar>
                      <v-card-actions class="flex-column align-start pa-0">
                        <v-card-title
                          class="title pa-0 pr-2 grey--text text--darken-2"
                        >
                          مـازدا مازدا3
                        </v-card-title>
                        <v-card-title
                          class="recount pa-0 pr-2 grey--text text--darken-1"
                        >
                          <span>021211 , (15 - 18) , احمر</span>
                        </v-card-title>
                      </v-card-actions>
                      <v-spacer></v-spacer>
                      <div>
                        <v-btn class="d-block mx-auto" icon>
                          <v-icon>mdi-trash-can</v-icon>
                        </v-btn>
                        <v-sheet class="justify-center">
                          <v-card
                            style="overflow: hidden; margin: 0 auto"
                            outlined
                            max-width="120"
                            height="30"
                          >
                            <v-card-actions class="pa-0">
                              <v-btn
                                class="px-1"
                                tile
                                elevation="0"
                                height="30"
                                min-width="30"
                                @click="Quantity++"
                              >
                                <v-icon size="15" color="grey darken-2">
                                  mdi-plus
                                </v-icon>
                              </v-btn>
                              <v-text-field
                                solo
                                dense
                                flat
                                v-model="Quantity"
                                hide-details
                                class="text-center"
                                type="number"
                              ></v-text-field>
                              <v-btn
                                class="px-1"
                                tile
                                elevation="0"
                                height="30"
                                min-width="30"
                                @click="Quantity--"
                              >
                                <v-icon size="15" color="grey darken-2">
                                  mdi-minus
                                </v-icon>
                              </v-btn>
                            </v-card-actions>
                          </v-card>
                        </v-sheet>
                      </div>
                      <v-spacer></v-spacer>
                      <v-card-actions
                        class="flex-column align-center my-auto pa-0"
                      >
                        <v-card-title class="price pa-0 px-2 red--text">
                          10254<span class="mr-1">ريال</span>
                        </v-card-title>
                      </v-card-actions>
                    </v-card-actions>
                  </v-card>
                </v-sheet>
              </v-col>
            </v-row>
          </v-col>
          <v-col>
            <v-banner
              sticky
              rounded=""
              class="mx-2 pa-0"
              elevation="2"
              min-height="180"
            >
              <v-card-actions class="justify-space-between">
                <v-checkbox
                  hide-details
                  class="ma-0 pa-0"
                  v-model="checkbox"
                  label="أختيار الكل"
                ></v-checkbox>
                <v-btn elevation="0" small class="btn2">
                  <v-icon size="15" color="red lighten-2" right>
                    mdi-trash-can
                  </v-icon>
                  حذف الكل
                </v-btn>
              </v-card-actions>
              <!-- <v-subheader>ملخص الطلب</v-subheader> -->
              <span class="pa-2 d-block location">
                <v-icon color="blue lighten-2" right size="20">
                  mdi-map-marker
                </v-icon>
                إجمالي الطلبات إجمالي الطلبات ,85544 إجمالي الطلبات إجمالي
                الطلبات ,85544
              </span>
              <v-divider></v-divider>
              <v-card-actions class="">
                <v-card-text class="pa-0 check-out">
                  إجمالي الطلبات (
                  <span class="mx-1 red--text">{{ checkbox }}</span> )
                </v-card-text>
                <div class="d-flex">
                  <span class="mx-2 green--text">0.00</span> ريال
                </div>
              </v-card-actions>
              <v-card-actions class="justify-center px-0">
                <v-btn tile block class="btn1" elevation="0">شراء</v-btn>
              </v-card-actions>
            </v-banner>
          </v-col>
        </v-row>
      </v-sheet>
    </v-container>
  </div>
</template>
<script>
export default {
  name: "TheClientCartPage",
  data() {
    return {
      checkbox: 0,
      Quantity: 1,
    };
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";

.TheClientCartPage {
  width: 100%;
  min-height: 100vh;
  // padding: $padding;
  .cart-title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-size: 16px;
    color: $fontcolorlinks;
    pointer-events: none;

    .v-icon {
      font-size: 19px;
      color: $color-2;
    }
  }
  .title {
    font-family: $fontfamliy !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 16px !important;
    pointer-events: none;
  }
  .recount {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 12px !important;
    font-weight: 500;
    pointer-events: none;
  }
  .price {
    font-family: $fontfamliy2 !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 16px !important;
    font-weight: 500;
    pointer-events: none;
  }

  .check-out {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 600 !important;
    font-size: 15px !important;
    color: $fontcolorlinks;
  }
  .location {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 500 !important;
    font-size: 13px !important;
    color: $fontcolorlinks;
    pointer-events: none;
  }
  .store-name {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 600 !important;
    font-size: 13px !important;
    color: $fontcolorlinks;
    pointer-events: none;

    .v-icon {
      color: $color-2 !important;
      font-size: 20px !important;
    }
  }
  .btn1 {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-size: 15px !important;
    color: #fff;
    background-color: #1976d2 !important;
  }
  .btn2 {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 500 !important;
    font-size: 13px !important;
    color: rgb(106, 104, 104);
  }
}
::v-deep .theme--light.v-btn:hover:before {
  opacity: 0;
}
::v-deep .theme--light.v-btn:focus:before {
  background-color: transparent;
}
::v-deep label.v-label.theme--light {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-weight: 500 !important;
  font-size: 13.5px !important;
}
/* Chrome, Safari, Edge, Opera */
::v-deep input::-webkit-outer-spin-button,
::v-deep input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
/* Firefox */
::v-deep input[type="number"] {
  -moz-appearance: textfield;
}
::v-deep .v-text-field.v-text-field--solo.v-input--dense > .v-input__control {
  min-height: 27px !important;
}
::v-deep
  .v-input.text-center.v-input--hide-details.v-input--is-label-active.v-input--is-dirty.v-input--dense.theme--light.v-text-field.v-text-field--single-line.v-text-field--solo.v-text-field--solo-flat.v-text-field--is-booted.v-text-field--enclosed {
  min-height: 30px !important;
}
::v-deep .v-text-field.v-text-field--solo .v-input__control input {
  text-align: center;
}
::v-deep
  .v-text-field.v-text-field--enclosed:not(.v-text-field--rounded)
  > .v-input__control
  > .v-input__slot {
  padding: 0;
}
.addToCartAndChat-SmallScreen {
  .addToCartAndChat-SmallScreen-btn {
    background-color: transparent !important;
    font-family: $fontfamliy !important;
    letter-spacing: 0 !important;
    font-size: 14px !important;
    color: $fontcolorlinks;
    .v-icon {
      color: $color-2 !important;
    }
  }
}
::v-deep .v-banner__wrapper {
  padding: 0 !important;
  border: none !important;
}
</style>
