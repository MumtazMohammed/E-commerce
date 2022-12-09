<template>
  <div class="TheClientCartPage">
    <v-app-bar class="mb-5" app>
      <v-toolbar-title class="toolbar-title">
        <v-icon size="20">mdi-cart-plus</v-icon>
        سلة التسوق
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/TheUserPageView" icon>
        <v-icon size="30">mdi-arrow-left-thin</v-icon>
      </v-btn>
    </v-app-bar>
    <v-container class="mb-14 mt-13 px-1">
      <v-col cols="12" class="py-1">
        <v-sheet outlined class="pa-3">
          <v-card-actions class="pa-0">
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
            <v-btn small class="mr-0 store-name" elevation="0"> حذف </v-btn>
          </v-card-actions>
          <v-card class="pa-1">
            <v-card-actions class="justify-start flex-wrap align-start pa-0">
              <v-checkbox
                hide-details
                value="1"
                class="ma-0 pa-0"
                v-model="checkbox"
              ></v-checkbox>
              <v-img
                contain
                max-width="75"
                class="my-auto"
                src="@/assets/Mazda/mazda1.jpg"
                alt="@/assets/Hyundai/image2.jpg"
              ></v-img>
              <div>
                <span class="recount d-block pr-2 grey--text text--darken-2">
                  مـازدا مازدا3
                </span>
                <v-card-text
                  class="recount pa-0 pr-2 grey--text text--darken-1"
                >
                  <span class="mx-1"> 2 </span>
                  ,
                  <span class="mx-1"> احمر</span>
                  ,
                  <span class="mx-1"> ee02121</span>
                  ,
                  <span class="mx-1"> (15 - 18) </span>
                </v-card-text>
                <span class="price d-block my-auto pa-0 px-2 red--text">
                  10254
                  <span class="text-center">ريال</span>
                </span>
              </div>
            </v-card-actions>
          </v-card>
        </v-sheet>
      </v-col>
    </v-container>
    <v-sheet class="sheet px-2" height="70">
      <v-card-actions
        class="pa-0"
        style="width: 100%; justify-content: space-between; height: 100%"
      >
        <v-card
          flat
          tile
          style="display: flex; flex-direction: column; justify-content: center"
          height="100%"
        >
          <v-checkbox
            hide-details
            class="ma-0 pa-0"
            v-model="checkbox"
            label="أختيار الكل"
          ></v-checkbox>
          <v-card-text class="pa-1 pr-2 check-out">
            إجمالي الطلبات (
            <span class="mx-1 red--text">{{ checkbox }}</span> )
            <span class="mx-1 green--text">0.00</span> ريال
          </v-card-text>
        </v-card>
        <v-btn elevation="0" class="CheckOut">شراء</v-btn>
      </v-card-actions>
    </v-sheet>
  </div>
</template>
<script>
export default {
  name: "TheClientCartPage",
  data() {
    return {
      checkbox: 0,
      value: "recent",
    };
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";

.TheClientCartPage {
  width: 100%;
  min-height: 40vh;
  // padding: $padding;
  .toolbar-title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorlinks !important;
    font-size: 16px !important;
    font-weight: 600;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    .v-icon {
      color: $color-2 !important;
      margin-left: 5px;
    }
  }

  .recount {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 14px !important;
    pointer-events: none;
  }
  .price {
    font-family: $fontfamliy2 !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 14px !important;
    font-weight: 500;
  }

  .check-out {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 600 !important;
    font-size: 15px !important;
    color: $fontcolorlinks;
  }
  .store-name {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 600 !important;
    font-size: 13px !important;
    color: $fontcolorlinks;
    .v-icon {
      color: $color-2 !important;
      font-size: 20px !important;
    }
  }
  .chat-icon {
    color: $color-2 !important;
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
::v-deep .v-input--selection-controls__ripple {
  display: none;
}
::v-deep .v-input__slot {
  width: fit-content;
}
.sheet {
  position: fixed;
  bottom: 0;
  right: 0;
  left: 0;
  border-top: 1px solid #eee !important;
}
.CheckOut {
  background-color: $color-2 !important;
  font-family: $fontfamliy3;
  letter-spacing: 0;
  color: #fff !important;
  font-size: 14px !important;
}
</style>
