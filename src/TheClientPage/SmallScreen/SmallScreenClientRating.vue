<template>
  <div class="TheClientCartPage">
    <v-app-bar class="mb-5" app hide-on-scroll>
      <v-toolbar-title class="toolbar-title">
        <v-icon right>mdi-star</v-icon>
        تقييماتي
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/TheUserPageView" icon>
        <v-icon size="30">mdi-arrow-left-thin</v-icon>
      </v-btn>
    </v-app-bar>
    <v-container class="mt-13 px-1">
      <v-sheet v-for="item in 15" :key="item" elevation="2" class="pa-2 my-1">
        <v-card-text class="pa-1 mb-2 store-name">
          <v-icon right>mdi-store-outline </v-icon>
          وقت العطور
        </v-card-text>
        <v-card outlined class="pa-1">
          <v-card-actions class="pa-0">
            <v-checkbox
              hide-details
              value="1"
              class="ma-0 pa-0"
              v-model="checkbox"
            ></v-checkbox>
            <v-spacer></v-spacer>
            <v-btn color="transparent" icon small elevation="0">
              <v-icon class="red--text text--lighten-2">mdi-close</v-icon>
            </v-btn>
          </v-card-actions>
          <v-card-actions class="justify-start align-start pa-0">
            <v-img
              contain
              max-width="100"
              src="@/assets/Mazda/mazda1.jpg"
              alt="@/assets/Hyundai/image2.jpg"
            ></v-img>
            <v-card-actions
              style="height: 75px; justify-content: space-between"
              class="flex-column align-start pa-0"
            >
              <span class="recount d-block pr-2 grey--text text--darken-2">
                مـازدا مازدا3
              </span>
              <div class="recount d-flex pa-0 pr-1 grey--text text--darken-1">
                <div class="mx-1">لون (<span class="mx-1">أحمر</span>)</div>
                <div class="mx-1">موديل (<span class="mx-1">ET6897</span>)</div>
                <div class="mx-1">عدد (<span class="mx-1">2</span>)</div>
              </div>
              <span class="price d-block pa-0 pr-2 red--text">
                10254<span class="mr-1">ريال</span>
              </span>
            </v-card-actions>
          </v-card-actions>
        </v-card>
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
  min-height: 100vh;
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
  .title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 13px !important;
  }
  .recount {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 13px !important;
    font-weight: 600;
  }
  .price {
    font-family: $fontfamliy2 !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 16px !important;
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
  .btn1 {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 500 !important;
    font-size: 14px !important;
    color: $fontcolorsm;
    background-color: $color-2 !important;
  }
  .btn2 {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 500 !important;
    font-size: 16px !important;
    color: rgb(106, 104, 104);
    background-color: transparent !important;
    // border: 1px solid rgb(222, 222, 222);
  }
  .btn2:hover {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 500 !important;
    font-size: 16px !important;
    color: rgb(240, 27, 27);
    background-color: transparent !important;
    // border: 1px solid rgb(222, 222, 222);
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
}
.CheckOut {
  background-color: $color-2 !important;
  font-family: $fontfamliy3;
  letter-spacing: 0;
  color: #fff !important;
  font-size: 16px !important;
}
</style>
