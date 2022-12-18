<template>
  <div class="SellerStore">
    <v-card
      style="overflow: hidden"
      class="overflow-hidden card-info"
      color="grey lighten-3"
    >
      <v-row no-gutters>
        <div style="display: flex; flex-direction: column; justify-content: ">
          <v-avatar class="profile" color="grey" size="150" tile>
            <v-img
              src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
            ></v-img>
          </v-avatar>
          <!-- store view -->
          <v-dialog persistent v-model="dialog" max-width="300px">
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                text
                dark
                tile
                small
                elevation="0"
                v-bind="attrs"
                v-on="on"
                class="info-sm info"
              >
                <v-icon> mdi-information-variant </v-icon>
              </v-btn>
            </template>
            <v-card>
              <v-card-title class="store-view">
                <v-icon right size="23"> mdi-information-outline </v-icon>
                حول المتجر
              </v-card-title>
              <v-divider></v-divider>
              <v-card-text style="height: 300px">
                <ul class="pl-0 pr-0">
                  <li>
                    <v-icon color="grey  darken-1" right size="20">
                      mdi-package
                    </v-icon>
                    المنتجات : <span class="deep-orange--text">44</span>
                  </li>
                  <li>
                    <v-icon color="grey  darken-1" right size="20">
                      mdi-account-group
                    </v-icon>
                    المتابعين : <span class="deep-orange--text">44</span>
                  </li>
                  <li>
                    <v-icon color="grey  darken-1" right size="20">
                      mdi-file-cancel
                    </v-icon>
                    معدل الإلغاء : <span class="deep-orange--text">44</span>
                  </li>
                  <li>
                    <v-icon color="grey  darken-1" right size="20">
                      mdi-star
                    </v-icon>
                    تقييم المتجر : <span class="deep-orange--text">44</span>
                  </li>
                  <li>
                    <v-icon color="grey  darken-1" right size="20">
                      mdi-account-clock
                    </v-icon>
                    انضم : <span class="deep-orange--text">44</span>
                  </li>
                  <li>
                    <v-icon color="grey  darken-1" right size="20">
                      mdi-forum-outline
                    </v-icon>
                    أداء الدردشة: : <span class="deep-orange--text">44</span>
                  </li>
                </ul>
              </v-card-text>
              <v-divider></v-divider>
              <v-card-actions>
                <v-btn
                  color="blue darken-1"
                  class="btn"
                  text
                  @click="dialog = false"
                >
                  إغلاق
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-dialog>
        </div>
        <v-col class="info-lg" cols="3">
          <v-sheet
            color="transparent"
            style="display: flex; flex-direction: column"
            class="mr-3 fill-height"
          >
            <v-card-text class="pa-0 pb-2 StoreName">
              إلكترونيات برو
            </v-card-text>
            <span class="StoreLastSeen"> إلكترونيات برو </span>
            <v-spacer></v-spacer>
            <v-btn-toggle
              background-color="transparent"
              tile
              borderless
              class="justify-center"
              dense
            >
              <v-btn color="transparent" width="50%">
                <span class="btn">تابع</span>
                <v-icon right> mdi-account </v-icon>
              </v-btn>
              <v-btn color="transparent" width="50%">
                <span class="btn">مراسلة</span>
                <v-icon right> mdi-forum-outline </v-icon>
              </v-btn>
            </v-btn-toggle>
          </v-sheet>
        </v-col>
        <v-col class="info-sm">
          <div class="pa-2">
            <v-card-text class="pa-0 pb-2 StoreName">
              إلكترونيات برو
            </v-card-text>
            <span class="StoreLastSeen"> إلكترونيات برو </span>
          </div>
          <v-card-actions
            no-gutters
            style="align-items: flex-end; height: 56% !important"
            class="fill-height justify-center py-1"
          >
            <v-btn width="45%" elevation="0" class="">
              <span class="btn">تابع</span>
              <v-icon right color="blue"> mdi-account </v-icon>
            </v-btn>
            <v-btn width="45%" elevation="0" class="">
              <span class="btn">مراسلة</span>
              <v-icon right color="green"> mdi-forum-outline </v-icon>
            </v-btn>
          </v-card-actions>
        </v-col>
        <v-spacer class="info-lg"></v-spacer>
        <div class="mr-3 info-lg">
          <ul class="pl-0 pr-6">
            <li>
              <v-icon color="grey  darken-1" right size="20">
                mdi-package
              </v-icon>
              المنتجات : <span class="deep-orange--text">44</span>
            </li>
            <li>
              <v-icon color="grey  darken-1" right size="20">
                mdi-account-group
              </v-icon>
              المتابعين : <span class="deep-orange--text">44</span>
            </li>
            <li>
              <v-icon color="grey  darken-1" right size="20">
                mdi-file-cancel
              </v-icon>
              معدل الإلغاء : <span class="deep-orange--text">44</span>
            </li>
          </ul>
        </div>
        <div class="mr-3 ml-3 info-lg">
          <ul class="pl-0 pr-6">
            <li>
              <v-icon color="grey  darken-1" right size="20"> mdi-star </v-icon>
              تقييم المتجر : <span class="deep-orange--text">44</span>
            </li>
            <li>
              <v-icon color="grey  darken-1" right size="20">
                mdi-account-clock
              </v-icon>
              انضم : <span class="deep-orange--text">44</span>
            </li>
            <li>
              <v-icon color="grey  darken-1" right size="20">
                mdi-forum-outline
              </v-icon>
              أداء الدردشة: : <span class="deep-orange--text">44</span>
            </li>
          </ul>
        </div>
      </v-row>
    </v-card>
  </div>
</template>

<script>
import Services from "../data-json/showroom.json";
export default {
  name: "ServicesPage",
  components: {},
  data() {
    return {
      Services,
      dialog: false,
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
.SellerStore {
  .card-info {
    @media (max-width: 700px) {
      box-shadow: none !important;
      border-radius: 0 !important;
    }
  }
  .StoreName {
    font-family: $fontfamliy3;
    font-size: 15px !important;
    letter-spacing: 0 !important;
  }
  .StoreLastSeen {
    font-size: 13px !important;
  }
}
.btn {
  letter-spacing: 0 !important;
  font-size: 16px !important;
  font-weight: 500 !important;
  font-family: $fontfamliy3 !important;
  color: $fontcolorlinks;
  // color: $fontcolor !important;
}
ul {
  list-style: none !important;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  letter-spacing: 0 !important;
  font-size: 15px !important;
  font-weight: 500 !important;
  font-family: $fontfamliy3 !important;
  color: $fontcolor !important;
  @media (max-width: 700px) {
    font-size: 16px !important;
  }
  span {
    margin-right: 5px;
  }
}
.store-view {
  font-size: 17px !important;
  font-weight: 600 !important;
  font-family: $fontfamliy3 !important;
  color: $fontcolorlinks;
  letter-spacing: 0 !important;
  @media (max-width: 600px) {
    font-size: 15px !important;
  }
  .v-icon {
    color: $color-2 !important;
  }
}
::v-deep.v-avatar.profile.rounded-0.grey {
  border-radius: 3px !important;
  overflow: hidden !important;
  margin: auto 0;

  @media (max-width: 700px) {
    height: 133px !important;
    min-width: 130px !important;
    width: 130px !important;
    margin: 0;
    border-radius: 0px !important;
  }
}
.info-lg {
  @media (max-width: 700px) {
    display: none;
  }
}
.info-sm {
  display: none;
  @media (max-width: 700px) {
    display: block;
  }
}
</style>
