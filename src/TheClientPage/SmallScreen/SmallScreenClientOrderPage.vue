<template>
  <div class="UserAdd">
    <v-app-bar class="mb-5" app>
      <v-toolbar-title class="toolbar-title">
        <v-icon size="20">mdi-shopping</v-icon>
        مشترياتي
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/TheUserPageView" icon>
        <v-icon size="30">mdi-arrow-left-thin</v-icon>
      </v-btn>
    </v-app-bar>
    <v-tabs-items v-model="tab" class="mt-16 mb-14">
      <!-- All  -->
      <v-tab-item style="height: 82vh; overflow-y: scroll" value="tab-1">
        <v-col cols="12" class="py-1">
          <v-sheet outlined class="pa-1">
            <v-card-actions class="pa-0">
              <v-card-text class="pa-1 store-name">
                <v-icon right>mdi-store-outline </v-icon>
                وقت العطور
              </v-card-text>
              <v-btn icon>
                <v-icon class="chat-icon" size="20">mdi-message </v-icon>
              </v-btn>
            </v-card-actions>
            <v-card style="display: flex" class="pa-1" width="100%" tile>
              <v-avatar class="avatar" rounded size="60" color="#fff">
                <v-img
                  src="@/assets/Mazda/mazda1.jpg"
                  alt="@/assets/Hyundai/image2.jpg"
                ></v-img>
              </v-avatar>
              <div>
                <v-card-text class="title pa-0 pr-2 grey--text text--darken-2">
                  مـازدا مازدا3
                </v-card-text>
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
                <v-card-text class="price pa-0 pr-2 red--text">
                  10254<span class="mr-1">ريال</span>
                </v-card-text>
              </div>
              <!-- <v-card-title class="recount pa-0 pr-2 grey--text text--darken-1">
                *عدد (<span>55</span>)
              </v-card-title> -->
            </v-card>
            <v-card-actions class="pa-2">
              <v-btn block elevation="0" class="btn1"> الشراء مجدداً </v-btn>
            </v-card-actions>
          </v-sheet>
        </v-col>
        <v-col cols="12" class="py-1">
          <v-sheet outlined class="pa-1">
            <v-card-actions class="pa-0">
              <v-card-text class="pa-1 store-name">
                <v-icon right>mdi-store-outline </v-icon>
                وقت العطور
              </v-card-text>
              <v-btn icon>
                <v-icon class="chat-icon" size="20">mdi-message </v-icon>
              </v-btn>
              <v-btn small elevation="0"> إلغاء </v-btn>
            </v-card-actions>
            <v-card style="display: flex" class="pa-1" width="100%" tile>
              <v-avatar class="avatar" rounded size="60" color="#fff">
                <v-img
                  src="@/assets/Mazda/mazda1.jpg"
                  alt="@/assets/Hyundai/image2.jpg"
                ></v-img>
              </v-avatar>
              <div>
                <v-card-text class="title pa-0 pr-2 grey--text text--darken-2">
                  مـازدا مازدا3
                </v-card-text>
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
                <v-card-text class="price pa-0 pr-2 red--text">
                  10254<span class="mr-1">ريال</span>
                </v-card-text>
              </div>
              <!-- <v-card-title class="recount pa-0 pr-2 grey--text text--darken-1">
                *عدد (<span>55</span>)
              </v-card-title> -->
            </v-card>
            <!-- Progress  -->
            <v-card-actions class="px-0">
              <v-card-text class="stepper-Info pa-0 grey--text text--darken-2">
                <v-icon
                  size="16"
                  style="border-radius: 50%; width: 18px; height: 18px"
                  class="blue white--text"
                  right
                  dark
                >
                  mdi-check
                </v-icon>
                تم دفع ( <span>154</span> ريال)
              </v-card-text>
              <v-card-text class="stepper-Info pa-0 grey--text text--darken-2">
                <v-icon
                  size="16"
                  style="border-radius: 50%; width: 18px; height: 18px"
                  class="grey white--text"
                  right
                >
                  mdi-check
                </v-icon>
                تم شحن المنتج
              </v-card-text>
              <v-card-text class="stepper-Info pa-0 grey--text text--darken-2">
                <v-icon
                  size="16"
                  style="border-radius: 50%; width: 18px; height: 18px"
                  class="grey white--text"
                  right
                >
                  mdi-check
                </v-icon>
                تم توصيل المنتج
              </v-card-text>
            </v-card-actions>
          </v-sheet>
        </v-col>
        <v-col cols="12" class="py-1">
          <v-sheet outlined class="pa-1">
            <v-card-actions class="pa-0">
              <v-card-text class="pa-1 store-name">
                <v-icon right>mdi-store-outline </v-icon>
                وقت العطور
              </v-card-text>
              <v-btn icon>
                <v-icon class="chat-icon" size="20">mdi-message </v-icon>
              </v-btn>
            </v-card-actions>
            <v-card style="display: flex" class="pa-1" width="100%" tile>
              <v-avatar class="avatar" rounded size="60" color="#fff">
                <v-img
                  src="@/assets/Mazda/mazda1.jpg"
                  alt="@/assets/Hyundai/image2.jpg"
                ></v-img>
              </v-avatar>
              <div>
                <v-card-text class="title pa-0 pr-2 grey--text text--darken-2">
                  مـازدا مازدا3
                </v-card-text>
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
                <v-card-text class="price pa-0 pr-2 red--text">
                  10254<span class="mr-1">ريال</span>
                </v-card-text>
              </div>
              <!-- <v-card-title class="recount pa-0 pr-2 grey--text text--darken-1">
                *عدد (<span>55</span>)
              </v-card-title> -->
            </v-card>
            <v-card-actions class="pa-2 justify-space-between">
              <v-btn text elevation="0" class="btn1"> قـيـيـم المنتج</v-btn>
              <v-spacer></v-spacer>
              <span class="rate-text"> قيم الآن واحصل على 5 نقاط </span>
            </v-card-actions>
          </v-sheet>
        </v-col>
      </v-tab-item>
      <!-- shipping order  -->
      <v-tab-item style="height: 82vh; overflow-y: scroll" value="tab-2">
        <v-col cols="12" class="py-1">
          <v-sheet outlined class="pa-1">
            <v-card-actions class="pa-0">
              <v-card-text class="pa-1 store-name">
                <v-icon right>mdi-store-outline </v-icon>
                وقت العطور
              </v-card-text>
              <v-btn icon>
                <v-icon class="chat-icon" size="20">mdi-message </v-icon>
              </v-btn>
              <v-btn small elevation="0"> إلغاء </v-btn>
            </v-card-actions>
            <v-card style="display: flex" class="pa-1" width="100%" tile>
              <v-avatar class="avatar" rounded size="60" color="#fff">
                <v-img
                  src="@/assets/Mazda/mazda1.jpg"
                  alt="@/assets/Hyundai/image2.jpg"
                ></v-img>
              </v-avatar>
              <div>
                <v-card-text class="title pa-0 pr-2 grey--text text--darken-2">
                  مـازدا مازدا3
                </v-card-text>
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
                <v-card-text class="price pa-0 pr-2 red--text">
                  10254<span class="mr-1">ريال</span>
                </v-card-text>
              </div>
              <!-- <v-card-title class="recount pa-0 pr-2 grey--text text--darken-1">
                *عدد (<span>55</span>)
              </v-card-title> -->
            </v-card>
            <!-- Progress  -->
            <v-card-actions class="px-0">
              <v-card-text class="stepper-Info pa-0 grey--text text--darken-2">
                <v-icon
                  size="16"
                  style="border-radius: 50%; width: 18px; height: 18px"
                  class="blue white--text"
                  right
                  dark
                >
                  mdi-check
                </v-icon>
                تم دفع ( <span>154</span> ريال)
              </v-card-text>
              <v-card-text class="stepper-Info pa-0 grey--text text--darken-2">
                <v-icon
                  size="16"
                  style="border-radius: 50%; width: 18px; height: 18px"
                  class="grey white--text"
                  right
                >
                  mdi-check
                </v-icon>
                تم شحن المنتج
              </v-card-text>
              <v-card-text class="stepper-Info pa-0 grey--text text--darken-2">
                <v-icon
                  size="16"
                  style="border-radius: 50%; width: 18px; height: 18px"
                  class="grey white--text"
                  right
                >
                  mdi-check
                </v-icon>
                تم توصيل المنتج
              </v-card-text>
            </v-card-actions>
          </v-sheet>
        </v-col>
      </v-tab-item>
      <!-- completed shipping order  -->
      <v-tab-item style="height: 82vh; overflow-y: scroll" value="tab-3">
        <v-col cols="12" class="py-1">
          <v-sheet outlined class="pa-1">
            <v-card-actions class="pa-0">
              <v-card-text class="pa-1 store-name">
                <v-icon right>mdi-store-outline </v-icon>
                وقت العطور
              </v-card-text>
              <v-btn icon>
                <v-icon class="chat-icon" size="20">mdi-message </v-icon>
              </v-btn>
            </v-card-actions>
            <v-card style="display: flex" class="pa-1" width="100%" tile>
              <v-avatar class="avatar" rounded size="60" color="#fff">
                <v-img
                  src="@/assets/Mazda/mazda1.jpg"
                  alt="@/assets/Hyundai/image2.jpg"
                ></v-img>
              </v-avatar>
              <div>
                <v-card-text class="title pa-0 pr-2 grey--text text--darken-2">
                  مـازدا مازدا3
                </v-card-text>
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
                <v-card-text class="price pa-0 pr-2 red--text">
                  10254<span class="mr-1">ريال</span>
                </v-card-text>
              </div>
              <!-- <v-card-title class="recount pa-0 pr-2 grey--text text--darken-1">
                *عدد (<span>55</span>)
              </v-card-title> -->
            </v-card>
            <v-card-actions class="pa-2 justify-space-between">
              <v-btn text elevation="0" class="btn1"> قـيـيـم المنتج</v-btn>
              <v-spacer></v-spacer>
              <span class="rate-text"> قيم الآن واحصل على 5 نقاط </span>
            </v-card-actions>
          </v-sheet>
        </v-col>
      </v-tab-item>
      <!-- cancelled order  -->
      <v-tab-item style="height: 82vh; overflow-y: scroll" value="tab-4">
        <v-col cols="12" class="py-1" v-for="i in 8" :key="i">
          <v-sheet outlined class="pa-1">
            <v-card-actions class="pa-0">
              <v-card-text class="pa-1 store-name">
                <v-icon right>mdi-store-outline </v-icon>
                وقت العطور
              </v-card-text>
              <v-btn icon>
                <v-icon class="chat-icon" size="20">mdi-message </v-icon>
              </v-btn>
            </v-card-actions>
            <v-card style="display: flex" class="pa-1" width="100%" tile>
              <v-avatar class="avatar" rounded size="60" color="#fff">
                <v-img
                  src="@/assets/Mazda/mazda1.jpg"
                  alt="@/assets/Hyundai/image2.jpg"
                ></v-img>
              </v-avatar>
              <div>
                <v-card-text class="title pa-0 pr-2 grey--text text--darken-2">
                  مـازدا مازدا3
                </v-card-text>
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
                <v-card-text class="price pa-0 pr-2 red--text">
                  10254<span class="mr-1">ريال</span>
                </v-card-text>
              </div>
              <!-- <v-card-title class="recount pa-0 pr-2 grey--text text--darken-1">
                *عدد (<span>55</span>)
              </v-card-title> -->
            </v-card>
            <v-card-actions class="pa-2">
              <v-btn block elevation="0" class="btn1"> الشراء مجدداً </v-btn>
            </v-card-actions>
          </v-sheet>
        </v-col>
      </v-tab-item>
    </v-tabs-items>
    <v-bottom-navigation
      v-model="value"
      height="48"
      background-color="white"
      light
      hide-on-scroll
      fixed
    >
      <v-tabs
        hide-slider
        rounded="lg"
        v-model="tab"
        class="rounded-t-lg"
        centered
        grow
        background-color="white"
      >
        <v-tab href="#tab-1" active-class="links-active" class="links">
          الكل
        </v-tab>
        <v-tab href="#tab-2" active-class="links-active" class="links">
          الشحن
        </v-tab>
        <v-tab href="#tab-3" active-class="links-active" class="links">
          مكتمل
        </v-tab>
        <v-tab href="#tab-4" active-class="links-active" class="links">
          ملغي
        </v-tab>
      </v-tabs>
    </v-bottom-navigation>
  </div>
</template>
<script>
export default {
  name: "UserAdd",
  components: {},
  data() {
    return {
      text: "هل أنت متأكد من حذف الأعلان.",
      tab: null,
    };
  },
  methods: {
    customFilter(item, queryText) {
      const textOne = item.name.toLowerCase();
      const textTwo = item.abbr.toLowerCase();
      const searchText = queryText.toLowerCase();

      return (
        textOne.indexOf(searchText) > -1 || textTwo.indexOf(searchText) > -1
      );
    },
    save() {
      this.hasSaved = true;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.UserAdd {
  width: 100%;
  // padding: $padding;
  min-height: 80vh;
  .title {
    font-family: $fontfamliy !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 16px !important;
  }
  .recount {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 14px !important;
  }
  .price {
    font-family: $fontfamliy2 !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 14px !important;
    font-weight: 500;
  }
  .links {
    font-family: $fontfamliy !important;
    letter-spacing: 0;
    font-weight: 500;
    font-size: 16px !important;
  }

  .links-active {
    background-color: $color-2 !important;
    color: #ffffff;
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
  .btn1 {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    font-weight: 500 !important;
    font-size: 14px !important;
    color: $fontcolorlinks;
  }
  .btn2 {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 500 !important;
    font-size: 13px !important;
    color: $fontcolorlinks;
    background-color: transparent !important;
    border: 1px solid rgb(222, 222, 222);
  }
  .rate-text {
    font-family: $fontfamliy !important;
    letter-spacing: 0;
    // font-weight: 500 !important;
    font-size: 13px !important;
    color: $color-6;
  }
  // .oreder-CANCELLED {
  //   font-family: $fontfamliy3 !important;
  //   letter-spacing: 0;
  //   font-weight: 500 !important;
  //   font-size: 16px !important;
  //   color: #ffffff !important;
  //   background-color: #e53935;
  // }
}
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
.stepper-Info {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  font-weight: 500 !important;
  font-size: 12px !important;
  color: $fontcolorlinks !important;
  text-align: center;
}
::v-deep span.v-stepper__step__step.primary {
  background-color: $color-2 !important;
  border-color: $color-2 !important;
}
::v-deep .theme--light.v-stepper .v-stepper__step--complete .v-stepper__label {
  color: $color-2 !important;
}
::v-deep .theme--light.v-tabs .v-tab:hover:before {
  opacity: 0 !important;
}
::v-deep span.v-stepper__step__step {
  margin-left: 0;
  margin-bottom: 10px;
}
</style>
