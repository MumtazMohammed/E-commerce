<template>
  <div class="UserAdd pb-4">
    <!-- car card  -->
    <v-container>
      <v-tabs
        rounded="dm"
        v-model="tab"
        slider-size="2"
        slider-color="#fc624d"
        class="rounded-sm overflow-hidden"
        centered
        grow
        background-color="grey lighten-3"
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
      <v-tabs-items v-model="tab" class="mt-2">
        <!-- All  -->
        <v-tab-item value="tab-1">
          <v-row>
            <v-col cols="12" md="6" lg="4">
              <v-sheet
                style="display: flex; flex-direction: column"
                height="100%"
                outlined
                class="pa-1"
              >
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
                <v-card-actions
                  style="border-top: 1px solid #eee; width: 100%"
                  class="justify-start align-start"
                >
                  <v-avatar class="avatar" rounded size="80" color="#fff">
                    <v-img
                      src="@/assets/Mazda/mazda1.jpg"
                      alt="@/assets/Hyundai/image2.jpg"
                    ></v-img>
                  </v-avatar>
                  <v-card
                    style="
                      height: 79px;
                      display: flex;
                      justify-content: space-between;
                    "
                    width="100%"
                    class="flex-column"
                    tile
                    flat
                  >
                    <div>
                      <v-card-text
                        class="title pa-0 pr-2 grey--text text--darken-2"
                      >
                        مـازدا مازدا3
                      </v-card-text>
                      <v-card-text
                        class="recount pa-0 pr-2 grey--text text--darken-1"
                      >
                        *عدد (<span>55</span>)
                      </v-card-text>
                    </div>
                    <div>
                      <v-card-text class="price text-end pa-0 pr-2 red--text">
                        10254<span class="mr-1">ريال</span>
                      </v-card-text>
                    </div>
                  </v-card>
                </v-card-actions>
                <v-spacer></v-spacer>
                <!-- Progress  -->
                <v-card-actions class="">
                  <v-card-text
                    class="stepper-Info pa-0 grey--text text--darken-2"
                  >
                    <v-icon
                      size="16"
                      style="border-radius: 50%; width: 15px; height: 15px"
                      class="blue white--text"
                      right
                      dark
                    >
                      mdi-check
                    </v-icon>
                    تم دفع ( <span>154</span> ريال)
                  </v-card-text>
                  <v-card-text
                    class="stepper-Info pa-0 grey--text text--darken-2"
                  >
                    <v-icon
                      size="16"
                      style="border-radius: 50%; width: 15px; height: 15px"
                      class="grey white--text"
                      right
                    >
                      mdi-check
                    </v-icon>
                    تم شحن المنتج
                  </v-card-text>
                  <v-card-text
                    class="stepper-Info pa-0 grey--text text--darken-2"
                  >
                    <v-icon
                      size="16"
                      style="border-radius: 50%; width: 15px; height: 15px"
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
            <v-col cols="12" md="6" lg="4">
              <v-sheet
                style="display: flex; flex-direction: column"
                outlined
                class="ma-1 pa-1"
              >
                <v-card-actions class="pa-0">
                  <v-card-text class="pa-1 store-name">
                    <v-icon right>mdi-store-outline </v-icon>
                    وقت العطور
                  </v-card-text>
                  <v-btn icon>
                    <v-icon class="chat-icon" size="20">mdi-message </v-icon>
                  </v-btn>
                </v-card-actions>
                <v-card-actions
                  style="border-top: 1px solid #eee; width: 100%"
                  class="justify-start align-start"
                >
                  <v-avatar class="avatar" rounded size="80" color="#fff">
                    <v-img
                      src="@/assets/Mazda/mazda1.jpg"
                      alt="@/assets/Hyundai/image2.jpg"
                    ></v-img>
                  </v-avatar>
                  <v-card
                    style="
                      height: 79px;
                      display: flex;
                      justify-content: space-between;
                    "
                    width="100%"
                    class="flex-column"
                    tile
                    flat
                  >
                    <div>
                      <v-card-text
                        class="title pa-0 pr-2 grey--text text--darken-2"
                      >
                        مـازدا مازدا3
                      </v-card-text>
                      <v-card-text
                        class="recount pa-0 pr-2 grey--text text--darken-1"
                      >
                        *عدد (<span>55</span>)
                      </v-card-text>
                    </div>
                    <div>
                      <v-card-text class="price text-end pa-0 pr-2 red--text">
                        10254<span class="mr-1">ريال</span>
                      </v-card-text>
                    </div>
                  </v-card>
                </v-card-actions>
                <v-spacer></v-spacer>
                <v-card-actions class="pa-2 justify-space-between">
                  <v-btn text elevation="0" class="btn1"> قـيـيـم المنتج</v-btn>
                  <v-spacer></v-spacer>
                  <span class="rate-text"> قيم الآن واحصل على 5 نقاط </span>
                </v-card-actions>
              </v-sheet>
            </v-col>
            <v-col cols="12" md="6" lg="4">
              <v-sheet
                style="display: flex; flex-direction: column"
                outlined
                class="ma-1 pa-1"
              >
                <v-card-actions class="pa-0">
                  <v-card-text class="pa-1 store-name">
                    <v-icon right>mdi-store-outline </v-icon>
                    وقت العطور
                  </v-card-text>
                  <v-btn icon>
                    <v-icon class="chat-icon" size="20">mdi-message </v-icon>
                  </v-btn>
                </v-card-actions>
                <v-card-actions
                  style="border-top: 1px solid #eee; width: 100%"
                  class="justify-start align-start"
                >
                  <v-avatar class="avatar" rounded size="80" color="#fff">
                    <v-img
                      src="@/assets/Mazda/mazda1.jpg"
                      alt="@/assets/Hyundai/image2.jpg"
                    ></v-img>
                  </v-avatar>
                  <v-card
                    style="
                      height: 79px;
                      display: flex;
                      justify-content: space-between;
                    "
                    width="100%"
                    class="flex-column"
                    tile
                    flat
                  >
                    <div>
                      <v-card-text
                        class="title pa-0 pr-2 grey--text text--darken-2"
                      >
                        مـازدا مازدا3
                      </v-card-text>
                    </div>
                    <div>
                      <v-card-text class="price text-end pa-0 pr-2 red--text">
                        10254<span class="mr-1">ريال</span>
                      </v-card-text>
                    </div>
                  </v-card>
                </v-card-actions>
                <v-spacer></v-spacer>
                <v-card-actions class="pa-2">
                  <v-btn block elevation="0" class="btn1">
                    الشراء مجدداً
                  </v-btn>
                </v-card-actions>
              </v-sheet>
            </v-col>
          </v-row>
        </v-tab-item>
        <!-- shipping order  -->
        <v-tab-item value="tab-2">
          <v-row no-gutters>
            <v-col cols="6" v-for="i in 3" :key="i">
              <v-sheet outlined class="pa-1 ma-1">
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

                <v-card style="display: flex" width="100%" tile class="pa-2">
                  <v-avatar class="avatar" rounded size="80" color="#fff">
                    <v-img
                      src="@/assets/Mazda/mazda1.jpg"
                      alt="@/assets/Hyundai/image2.jpg"
                    ></v-img>
                  </v-avatar>
                  <div>
                    <v-card-text
                      class="title pa-0 pr-2 grey--text text--darken-2"
                    >
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
                  </div>
                  <v-spacer></v-spacer>
                  <span class="price my-auto red--text">
                    10254<span class="mr-1">ريال</span>
                  </span>
                </v-card>
                <!-- Progress  -->
                <v-card-actions class="px-0">
                  <v-card-text
                    class="stepper-Info pa-0 grey--text text--darken-2"
                  >
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
                  <v-card-text
                    class="stepper-Info pa-0 grey--text text--darken-2"
                  >
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
                  <v-card-text
                    class="stepper-Info pa-0 grey--text text--darken-2"
                  >
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
          </v-row>
        </v-tab-item>
        <!-- completed shipping order  -->
        <v-tab-item value="tab-3">
          <v-row no-gutters>
            <v-col cols="6" v-for="i in 3" :key="i">
              <v-sheet outlined class="ma-1 pa-1">
                <v-card-actions class="pa-0">
                  <v-card-text class="pa-1 store-name">
                    <v-icon right>mdi-store-outline </v-icon>
                    وقت العطور
                  </v-card-text>
                  <v-btn icon>
                    <v-icon class="chat-icon" size="20">mdi-message </v-icon>
                  </v-btn>
                  <v-btn icon>
                    <v-icon color="red lighten-2" size="20">
                      mdi-trash-can
                    </v-icon>
                  </v-btn>
                </v-card-actions>
                <v-card style="display: flex" width="100%" tile class="pa-2">
                  <v-avatar class="avatar" rounded size="80" color="#fff">
                    <v-img
                      src="@/assets/Mazda/mazda1.jpg"
                      alt="@/assets/Hyundai/image2.jpg"
                    ></v-img>
                  </v-avatar>
                  <div>
                    <v-card-text
                      class="title pa-0 pr-2 grey--text text--darken-2"
                    >
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
                  </div>
                  <v-spacer></v-spacer>
                  <span class="price my-auto red--text">
                    10254<span class="mr-1">ريال</span>
                  </span>
                </v-card>
                <v-card-actions class="pa-2 py-0 justify-space-between">
                  <v-btn text elevation="0" class="btn1"> قـيـيـم المنتج</v-btn>
                  <v-spacer></v-spacer>
                  <span class="rate-text"> قيم الآن واحصل على 5 نقاط </span>
                </v-card-actions>
              </v-sheet>
            </v-col>
          </v-row>
        </v-tab-item>
        <!-- cancelled order  -->
        <v-tab-item value="tab-4">
          <v-row no-gutters>
            <v-col v-for="i in 3" :key="i">
              <v-sheet outlined class="ma-1 pa-1">
                <v-card-actions class="pa-0">
                  <v-card-text class="pa-1 store-name">
                    <v-icon right>mdi-store-outline </v-icon>
                    وقت العطور
                  </v-card-text>
                  <v-btn icon>
                    <v-icon class="chat-icon" size="20">mdi-message </v-icon>
                  </v-btn>
                </v-card-actions>
                <v-card style="display: flex" width="100%" tile class="pa-2">
                  <v-avatar class="avatar" rounded size="80" color="#fff">
                    <v-img
                      src="@/assets/Mazda/mazda1.jpg"
                      alt="@/assets/Hyundai/image2.jpg"
                    ></v-img>
                  </v-avatar>
                  <div style="width: 100%">
                    <v-card-text
                      class="title pa-0 pr-2 grey--text text--darken-2"
                    >
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
                    <v-card-text class="price pa-0 text-end red--text">
                      10254<span class="mr-1">ريال</span>
                    </v-card-text>
                  </div>
                </v-card>
                <v-card-actions class="pa-2">
                  <v-btn block elevation="0" class="btn1">
                    الشراء مجدداً
                  </v-btn>
                </v-card-actions>
              </v-sheet>
            </v-col>
          </v-row>
        </v-tab-item>
      </v-tabs-items>
    </v-container>
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
  min-height: calc(100vh - 60px);

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
    font-size: 13px !important;
    font-weight: 600;
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
  .links {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 600;
    font-size: 15px !important;
  }
  .links:hover {
    color: $color-2 !important;
  }
  .links-active {
    color: $color-2 !important;
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
    font-weight: 500 !important;
    font-size: 14px !important;
    color: #1e88e5;
    // background-color: $color-2 !important;
  }
  .rate-text {
    font-family: $fontfamliy !important;
    letter-spacing: 0;
    pointer-events: none;
    font-size: 13px !important;
    color: $color-6;
    pointer-events: none;
  }
}
.stepper-Info {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-weight: 600 !important;
  font-size: 12px !important;
  color: $fontcolorlinks !important;
  text-align: center;
  pointer-events: none;
}
::v-deep .theme--light.v-stepper .v-stepper__step--complete .v-stepper__label {
  color: $color-2 !important;
}
::v-deep .theme--light.v-tabs .v-tab:hover:before {
  opacity: 0 !important;
}
</style>
