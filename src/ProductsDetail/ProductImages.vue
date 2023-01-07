<template>
  <div class="product">
    <v-row no-gutters class="justify-space-around">
      <!-- small devices image -->
      <v-col xs="12" sm="12" md="6" class="hidden-sm-and-up">
        <div>
          <v-dialog
            class="overflow--hidden"
            v-model="dialog"
            fullscreen
            hide-overlay
            transition="dialog-bottom-transition"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-banner
                color="transparent"
                style="overflow: hidden; position: relative"
              >
                <v-carousel
                  v-model="customerIMageNo"
                  height="420px"
                  delimiter-icon="mdi-minus"
                  touch
                  :show-arrows="false"
                >
                  <v-carousel-item
                    v-for="(singleImage, x) in getCarInfo.images"
                    :key="x"
                  >
                    <v-card
                      width="420"
                      height="100%"
                      class="image-background-small-screen"
                      style=""
                      :img="getimageUrl(getCarInfo.folder, singleImage)"
                    ></v-card>
                    <v-img
                      v-bind="attrs"
                      v-on="on"
                      max-height="420"
                      :src="getimageUrl(getCarInfo.folder, singleImage)"
                    >
                    </v-img>
                    <v-chip
                      large
                      label
                      class="discount-tag rounded-t-0 rounded-r-0"
                    >
                      <v-row
                        no-gutters
                        style="flex-direction: column; justify-content: center"
                      >
                        <v-icon size="20" color="amber lighten-5"
                          >mdi-star</v-icon
                        >
                        <span>متميز</span>
                      </v-row>
                    </v-chip>
                  </v-carousel-item>
                </v-carousel>
                <v-row no-gutters justify="center" class="py-1">
                  <v-chip
                    color="grey lighten-1"
                    small
                    class="elevation-0 white--text"
                  >
                    {{ customerIMageNo + 1 }} |
                    {{ getCarInfo.images.length }}
                  </v-chip>
                </v-row>
              </v-banner>
            </template>
            <v-card flat tile color="grey darken-4" class="overflow--hidden">
              <v-toolbar tile dark flat color="grey darken-3">
                <v-btn icon dark @click="dialog = false">
                  <v-icon>mdi-close</v-icon>
                </v-btn>
                <v-spacer></v-spacer>
                <v-toolbar-title>
                  {{ customerIMageNo + 1 }} /
                  {{ getCarInfo.images.length }}
                </v-toolbar-title>
              </v-toolbar>
              <v-carousel
                v-model="customerIMageNo"
                height="85vh"
                width="100%"
                touch
                hide-delimiters
                :show-arrows="false"
                class="overflow--hidden px-1"
              >
                <v-carousel-item
                  v-for="(singleImage, x) in getCarInfo.images"
                  :key="x"
                >
                  <v-img :src="getimageUrl(getCarInfo.folder, singleImage)">
                  </v-img>
                </v-carousel-item>
              </v-carousel>
            </v-card>
          </v-dialog>
        </div>
      </v-col>
      <!-- big devices image -->
      <v-col xs="12" sm="12" md="6" class="big-screen-img white">
        <v-sheet class="overflow-hidden">
          <v-img
            v-if="
              ActiveImage.length < 1
                ? (ActiveImage = getimageUrl(
                    getCarInfo.folder,
                    getCarInfo.image
                  ))
                : ActiveImage
            "
            :src="ActiveImage"
            :lazy-src="ActiveImage"
            v-bind="attrs"
            v-on="on"
            class="ma-sm-auto white image"
            max-height="600px"
            height="400px"
            contain
          >
            <v-chip large label class="discount-tag">
              <v-row
                no-gutters
                style="flex-direction: column; justify-content: center"
              >
                <v-icon size="20" color="amber lighten-5">mdi-star</v-icon>
                <span>متميز</span>
              </v-row>
            </v-chip>
          </v-img>

          <!--clickable images changer-->
          <v-sheet class="mx-auto" elevation="0" max-width="800">
            <v-slide-group v-model="model" class="pa-0 mt-1" column mandatory>
              <v-slide-item
                v-for="(singleImage, x) in getCarInfo.images"
                :key="x"
                v-slot="{ active, toggle }"
              >
                <v-card
                  color="transparent"
                  class="ma-1 mt-3"
                  flat
                  @mouseover="toggle"
                >
                  <v-avatar tile width="80" height="40" color="transparent">
                    <v-img
                      :class="active ? '' : 'not-active-img'"
                      @mouseover="
                        ActiveImage = getimageUrl(
                          getCarInfo.folder,
                          singleImage
                        )
                      "
                      :src="getimageUrl(getCarInfo.folder, singleImage)"
                    />
                  </v-avatar>
                </v-card>
              </v-slide-item>
            </v-slide-group>
          </v-sheet>
        </v-sheet>
      </v-col>
      <!-- big screen Products ordered Info  -->
      <v-col
        cols="12"
        sm="12"
        md="6"
        lg="6"
        class="remov-p-from-col-box-all white"
      >
        <productInformation />
        <!-- Products ordered Info  -->
        <v-sheet class="pa-2 mt-0 hidden-xs-only">
          <v-card-actions>
            <p class="Colors-text grey--text text--darken-1">الألوان :</p>
            <v-chip-group active-class="select" tile class="mx-auto" column>
              <v-chip
                v-for="(singleImage, x) in getCarInfo.images"
                :key="x"
                class="px-1"
              >
                <v-img
                  width="60"
                  height="30"
                  @click="
                    ActiveImage = getimageUrl(getCarInfo.folder, singleImage)
                  "
                  :src="getimageUrl(getCarInfo.folder, singleImage)"
                />
              </v-chip>
            </v-chip-group>
          </v-card-actions>
          <v-card-actions>
            <p class="Colors-text grey--text text--darken-1">الألوان :</p>
            <v-chip-group active-class="select" column class="mx-auto">
              <v-chip small> Elevator </v-chip>
              <v-chip small> Washer / Dryer </v-chip>
              <v-chip small> Fireplace </v-chip>
            </v-chip-group>
          </v-card-actions>
          <v-card-actions>
            <p class="Colors-text grey--text text--darken-1">الألوان :</p>
            <v-chip-group active-class="select" column class="mx-auto">
              <v-chip small> Elevator </v-chip>
              <v-chip small> Washer / Dryer </v-chip>
              <v-chip small> Fireplace </v-chip>
            </v-chip-group>
          </v-card-actions>
          <v-card-actions class="justify-center">
            <p class="Colors-text mb-0 grey--text text--darken-1">الألوان :</p>
            <v-spacer></v-spacer>
            <v-card
              style="overflow: hidden; margin: 0 auto"
              outlined
              max-width="150"
            >
              <v-card-actions class="pa-0">
                <v-btn
                  class="px-1"
                  tile
                  elevation="0"
                  height="38"
                  min-width="35"
                >
                  <v-icon size="17">mdi-plus</v-icon>
                </v-btn>
                <v-text-field
                  solo
                  dense
                  flat
                  hide-details
                  type="number"
                ></v-text-field>
                <v-btn
                  class="px-1"
                  tile
                  elevation="0"
                  height="38"
                  min-width="35"
                >
                  <v-icon size="17">mdi-minus</v-icon>
                </v-btn>
              </v-card-actions>
            </v-card>
            <v-spacer></v-spacer>
          </v-card-actions>
          <v-card-actions class="justify-center">
            <v-btn elevation="0" width="48%" class="add-chat">
              <v-icon right>mdi-cart-plus</v-icon>
              إضافة الى السلة
            </v-btn>
            <v-btn width="48%" elevation="0" class="add-chat">
              <v-icon right>mdi-message-text</v-icon>
              مراسلة البائع
            </v-btn>
          </v-card-actions>
        </v-sheet>
        <!-- small screen Products ordered Info  -->
        <div class="addToCartAndChat-SmallScreen">
          <v-card tile flat color="#fff" class="" height="46">
            <v-card-actions class="justify-center">
              <v-btn
                @click="sheet = !sheet"
                elevation="0"
                class="addToCartAndChat-SmallScreen-btn"
                small
                width="48%"
              >
                <v-icon left>mdi-cart-outline</v-icon>
                إضافة الى السلة
              </v-btn>
              <v-divider vertical class="mx-2 py-2 grey lighten-2"></v-divider>
              <v-btn
                elevation="0"
                class="addToCartAndChat-SmallScreen-btn"
                small
                width="48%"
              >
                <v-icon left>mdi-chat-processing-outline</v-icon>
                مراسلة
              </v-btn>
            </v-card-actions>
            <div>
              <v-bottom-sheet v-model="sheet">
                <v-sheet class="text-center py-3" height="auto">
                  <v-row no-gutters>
                    <v-col cols="12">
                      <v-card-actions class="justify-start align-start">
                        <v-avatar rounded size="70" color="transparent">
                          <img
                            v-if="
                              ActiveImage.length < 1
                                ? (ActiveImage = getimageUrl(
                                    getCarInfo.folder,
                                    getCarInfo.image
                                  ))
                                : ActiveImage
                            "
                            :src="ActiveImage"
                            :lazy-src="ActiveImage"
                          />
                        </v-avatar>
                        <div>
                          <p
                            class="Product-name-text grey--text text--darken-1 d-inline-block text-truncate mr-2 ma-0"
                          >
                            {{ getCarInfo.company }} {{ getCarInfo.name }}
                            {{ getCarInfo.modle }}
                          </p>
                          <p
                            class="ma-0 mr-2 Colors-text d-block text-start grey--text text--darken-1"
                          >
                            المخزون : <span class="">40</span>
                          </p>
                        </div>
                      </v-card-actions>
                    </v-col>
                  </v-row>
                  <v-card flat color="" class="pa-2 pt-0">
                    <v-card-actions>
                      <p class="Colors-text grey--text text--darken-1">
                        الألوان :
                      </p>
                      <v-chip-group
                        active-class="select"
                        tile
                        class="mx-auto"
                        column
                      >
                        <v-chip
                          v-for="(singleImage, x) in getCarInfo.images"
                          :key="x"
                          class="px-1"
                        >
                          <v-img
                            width="50"
                            height="30"
                            @click="
                              ActiveImage = getimageUrl(
                                getCarInfo.folder,
                                singleImage
                              )
                            "
                            :src="getimageUrl(getCarInfo.folder, singleImage)"
                          />
                        </v-chip>
                      </v-chip-group>
                    </v-card-actions>
                    <v-card-actions>
                      <p class="Colors-text grey--text text--darken-1">
                        الألوان :
                      </p>
                      <v-chip-group
                        active-class="select"
                        column
                        class="mx-auto"
                      >
                        <v-chip small> Elevator </v-chip>
                        <v-chip small> Washer / Dryer </v-chip>
                        <v-chip small> Fireplace </v-chip>
                      </v-chip-group>
                    </v-card-actions>
                    <v-card-actions>
                      <p class="Colors-text grey--text text--darken-1">
                        الألوان :
                      </p>
                      <v-chip-group
                        active-class="select"
                        column
                        class="mx-auto"
                      >
                        <v-chip small> Elevator </v-chip>
                        <v-chip small> Washer / Dryer </v-chip>
                        <v-chip small> Fireplace </v-chip>
                      </v-chip-group>
                    </v-card-actions>
                    <v-card-actions>
                      <p class="Colors-text mb-0 grey--text text--darken-1">
                        العدد :
                      </p>
                      <v-card
                        style="overflow: hidden; margin: 0 auto"
                        outlined
                        max-width="150"
                      >
                        <v-card-actions class="pa-0">
                          <v-btn
                            class="px-1"
                            tile
                            elevation="0"
                            height="38"
                            min-width="35"
                            @click="Quantity++"
                          >
                            <v-icon size="18" color="grey darken-2">
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
                            height="38"
                            min-width="35"
                            @click="Quantity--"
                          >
                            <v-icon size="18" color="grey darken-2">
                              mdi-minus
                            </v-icon>
                          </v-btn>
                        </v-card-actions>
                      </v-card>
                    </v-card-actions>
                  </v-card>
                  <v-divider class="mb-2"></v-divider>
                  <v-card-actions class="justify-center">
                    <v-btn elevation="0" rounded width="150px" class="add-chat">
                      إضافة
                    </v-btn>
                    <v-btn
                      @click="sheet = false"
                      elevation="0"
                      rounded
                      width="150px"
                      class="add-chat"
                    >
                      إلغاء
                    </v-btn>
                  </v-card-actions>
                </v-sheet>
              </v-bottom-sheet>
            </div>
          </v-card>
        </div>
      </v-col>
    </v-row>
  </div>
</template>
<script>
import CarData from "../data-json/All-Car.json";
import productInformation from "./productInformation.vue";

// import Share from "./ShareSaveReport.vue";
export default {
  name: "ProductImages",
  components: { productInformation },
  data() {
    return {
      items: ["Foo", "Bar", "Fizz", "Buzz"],
      customerIMageNo: 0,
      slidesPerView: 1,
      ActiveImage: "",
      width: 300,
      sheet: false,
      Quantity: 1,
      dialog: false,
      GetCarData: CarData,
      model: null,
      carName: this.$route.params.carName,
      carId: this.$route.params.carId,
      swiperOption: {
        zoom: true,
        pagination: {
          el: ".swiper-pagination",
        },
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev",
        },
      },
    };
  },
  // this is help full to call the image inside folder and inject to the src
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
  // this computed to call the item by it info
  computed: {
    getCarInfo() {
      let Carinformation = "";
      for (let i = 0; i < this.GetCarData.length; i++) {
        if (this.GetCarData[i].id == this.carId) {
          Carinformation = this.GetCarData[i];
          break;
        }
      }
      return Carinformation;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
// @import "vue-inner-image-zoom/lib/vue-inner-image-zoom.css";

::v-deep .v-image.v-responsive.theme--light {
  align-items: center;
}
::v-deep .v-image.v-responsive.img.theme--light {
  align-items: center !important;
}
::v-deep .v-carousel__controls {
  height: 30px;
}
::v-deep .v-carousel__controls__item {
  margin: 0 !important;
}
.img-box {
  width: 100%;
  min-height: 100%;
  position: relative;
  background-color: black;
  padding: 20px 10px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.btn {
  position: absolute;
  z-index: 99;
  padding: 15px;
  .icon {
    font-size: 30px;
  }
}
.not-active-img {
  position: relative;
}
.not-active-img::after {
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  // z-index: 1;
  opacity: 0.5;
  background-color: black;
}
::v-deep .v-slide-group__next {
  min-width: 30px;
}
::v-deep .v-slide-group__prev {
  min-width: 30px;
}
::v-deep .v-slide-group__content {
  justify-content: center;
}

.how-many-imag {
  position: relative;
  bottom: 28px;
  right: 50%;
  transform: translateX(50%);
  min-width: 45px;
  background-color: rgb(53, 53, 53);
  display: flex;
  align-items: center;
  padding: 2px;
  justify-content: center;
  border-radius: 2px !important;
  color: rgb(255, 255, 255);
  pointer-events: none;
  z-index: 5000;
  span {
    font-size: 16px;
  }
}
.big-screen-img {
  @media (max-width: 600px) {
    display: none !important;
  }
}
.small-screen-img {
  padding: 0px !important ;
  @media (min-width: 600px) {
    display: none;
  }
}
.remov-p-from-col-box-all {
  @media (max-width: 600px) {
    padding-bottom: 0;
    padding-top: 0;
  }
}
.Colors-text {
  font-family: $fontfamliy3 !important;
  font-size: 16px;
  font-weight: 400;
  display: block;
  text-align: start;
  margin-bottom: 0;
  pointer-events: none;

  @media (max-width: 600px) {
    font-size: 14px !important;
  }
}
.Product-name-text {
  font-family: $fontfamliy3 !important;
  font-size: 16px;
  font-weight: 400;
  pointer-events: none;
}

::v-deep
  i.v-icon.notranslate.v-chip__filter.v-icon--left.material-icons.theme--light {
  margin-right: 0;
  color: $color-2;
}
::v-deep button.add-chat {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  color: $color-2;
  font-size: 15px;
}
::v-deep .v-chip.v-size--default {
  height: 30px;
  border-radius: 2px !important;
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
  height: 28px !important;
}
::v-deep .v-text-field.v-text-field--solo .v-input__control input {
  text-align: center;
}
.addToCartAndChat-SmallScreen {
  display: none;
  @media (max-width: 600px) {
    display: block;
  }
  .addToCartAndChat-SmallScreen-btn {
    background-color: transparent !important;
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    font-size: 14px !important;
    color: $fontcolorlinks;
    .v-icon {
      color: $color-2 !important;
    }
  }
}
// select
::v-deep .theme--light.v-chip--active:before {
  opacity: 0 !important;
}
::v-deep .v-banner__wrapper {
  padding: 1px !important;
}
::v-deep .v-banner__content {
  padding: 0px !important;
}
::v-deep .theme--dark.v-btn.v-btn--icon {
  color: #bbb;
}
::v-deep
  .theme--light.v-banner.v-sheet:not(.v-sheet--outlined):not(.v-sheet--shaped)
  .v-banner__wrapper {
  border: 0 !important;
}
.select {
  background-color: $color-2;
  color: #fff !important;
}
.discount-tag {
  background-color: $color-2 !important;
  color: #fff !important;
  font-size: 15px !important;
  // font-weight: 600;
  position: absolute;
  font-family: $fontfamliy3 !important;
  top: 0;
  right: 0;
  @media (max-width: 600px) {
    font-size: 12px !important;
  }
  .v-icon {
    @media (max-width: 600px) {
      font-size: 13px !important;
    }
  }
}
.image-background-small-screen {
  position: absolute;
  top: 0;
  right: 0;
  backdrop-filter: blur(10px);
}
.image-background-small-screen::after {
  position: absolute;
  content: "";
  top: 0;
  right: 0;
  width: 100%;
  height: 100%;
  background-color: #ffffffc1;
  // backdrop-filter: blur(5px);
}
</style>
