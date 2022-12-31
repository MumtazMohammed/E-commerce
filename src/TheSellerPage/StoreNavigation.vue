<template>
  <div>
    <div class="ShowRoomBtnsNavgition">
      <v-app-bar flat clipped-right color="#fff">
        <v-btn
          :to="{
            name: 'MainStorePage',
            params: { MyCar: 'إعلاناتي' },
          }"
          icon
          class="grey--text text--darken-2"
          v-bind="attrs"
          v-on="on"
        >
          <v-icon>mdi-home-outline</v-icon>
        </v-btn>
        <!-- smalll menu  -->
        <v-btn
          icon
          class="grey--text text--darken-2 hidden-sm-and-up"
          @click.stop="dialog = true"
        >
          <v-icon>mdi-dots-grid</v-icon>
        </v-btn>
        <v-dialog
          no-click-animation
          persistent
          v-model="dialog"
          max-width="300"
        >
          <v-card class="pa-3" color="grey lighten-3">
            <v-card-actions
              class="flex-wrap justify-space-around card-actions pa-0"
            >
              <v-card
                @click="dialog = false"
                rounded="lg"
                class="my-1 py-3 menu-card"
                v-for="item in MenuLinks"
                :key="item"
                link
                width="45%"
                exact-path
                :to="item.RouterName"
              >
                <v-card-actions class="pa-0 pt-1 justify-center">
                  <v-icon
                    :class="item.class"
                    class="icon"
                    v-text="item.icon"
                  ></v-icon>
                </v-card-actions>
                <span class="link" v-text="item.link"></span>
              </v-card>
            </v-card-actions>
            <v-card-actions>
              <v-btn
                color="grey  darken-1"
                class="close-dialog"
                outlined
                @click="dialog = false"
              >
                إغلاق
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
        <v-divider vertical class="mx-2 hidden-sm-and-down"></v-divider>
        <!-- store name and click to setting -->
        <v-card
          flat
          rounded="lg"
          class="hidden-xs-only"
          color="grey lighten-2"
          max-width="170px"
        >
          <v-card-actions class="pa-1">
            <v-avatar size="30" color="grey"> </v-avatar>
            <span class="mr-1 text-truncate user-name"
              >وقت العطور رررسسسسسسسر</span
            >
          </v-card-actions>
        </v-card>
        <v-spacer></v-spacer>
        <!-- chat  -->
        <!-- big screen chat  -->
        <v-btn
          class="hidden-xs-only"
          to="/SellerNotification"
          icon
          @click.stop="showMsg = !showMsg"
        >
          <v-badge color="red" dot overlap left bordered>
            <v-icon>mdi-bell-outline</v-icon>
          </v-badge>
        </v-btn>
        <!-- small screen chat  -->
        <v-btn
          class="hidden-sm-and-up"
          :to="{
            name: 'SmallScreenNotification',
            params: { Notfication: 'الأشعارات' },
          }"
          icon
          @click.stop="showMsg = !showMsg"
        >
          <v-badge color="red" dot overlap left bordered>
            <v-icon>mdi-bell-outline</v-icon>
          </v-badge>
        </v-btn>
        <!-- go to main page  -->
        <v-btn icon to="/" class="tab" exact-path>
          <v-icon>mdi-arrow-left </v-icon>
        </v-btn>
      </v-app-bar>
      <!-- navigation menu   -->
      <v-sheet class="py-2 px-1 hidden-xs-only">
        <v-chip-group mandatory active-class="blue--text text--accent-4">
          <v-chip
            class="link"
            v-text="item.link"
            :to="item.RouterName"
            v-for="item in MenuLinks"
            :key="item"
          >
          </v-chip>
        </v-chip-group>
      </v-sheet>
    </div>
  </div>
</template>
<script>
export default {
  name: "ShowRoomBtnsNavgition",
  data() {
    return {
      drawer: false,
      group: null,
      dialog: false,
      showMsg: false,
      show: false,
      MenuLinks: [
        {
          link: "منتجاتي",
          icon: "mdi-package-variant",
          class: "MyProduct",
          RouterName: "/StoreProducts",
        },
        {
          link: "مبيعاتي",
          icon: "mdi-point-of-sale",
          class: "MySales",
          RouterName: "/MyOrder",
        },
        {
          link: "الدخل",
          icon: "mdi-cash",
          class: "MyIncome",
          RouterName: "/StoreIncome",
        },
        {
          link: "رؤى الأعمال",
          icon: "mdi-finance",
          class: "MyBusinessInsights",
          RouterName: "/BusinessInsights",
        },
        {
          link: "تسويق",
          icon: "mdi-percent-circle",
          class: "MyMarketingCentre",
          RouterName: "/Marketing",
        },
        {
          link: "إعدادات المتجر",
          icon: "mdi-cog-outline",
          class: "ShopSettings",
          RouterName: "/StoreProfile",
        },
      ],
    };
  },
  watch: {
    group() {
      this.drawer = false;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.ShowRoomBtnsNavgition {
  width: 100%;
  height: auto;
  position: relative;
}
.menu-card {
  height: 80px;
  width: 90px;
  @media (max-width: 600px) {
    height: 100px;
    width: 85px;
  }
}
.tab {
  color: $color-2 !important;
  font-size: 18px !important;
  font-weight: 600px;
  letter-spacing: 0 !important;
}
.main-page::v-deep .v-slide-group__content.v-tabs-bar__content {
  justify-content: flex-end;
}

.user-name {
  font-size: 13px;
  font-weight: 600;
  letter-spacing: 0;
  color: $fontcolorlinks;
  font-family: $fontfamliy3;
}

.card-actions {
  width: 100%;
}
.link {
  font-size: 14px !important;
  font-weight: 500;
  letter-spacing: 0;
  color: $fontcolorlinks !important;
  font-family: $fontfamliy3;
  text-align: center !important;
  @media (max-width: 600px) {
    margin-top: 9px;
    font-size: 13px !important;
    display: block;
  }
}
.icon {
  font-size: 26px !important;
  border-radius: 50%;
  padding: 8px;
  color: #fff !important;
}
.close-dialog {
  font-family: $fontfamliy3 !important;
  font-size: 14px !important;
  letter-spacing: 0 !important;
  font-weight: 600;
}
.MyProduct {
  background: linear-gradient(30deg, #536dfe 50%, #8c9eff 100%);
}
.MySales {
  background: linear-gradient(30deg, #f57c00 50%, #fb8c00 100%);
}
.MyBusinessInsights {
  background: linear-gradient(30deg, #00b0ff 50%, #40c4ff 100%);
}
.MyMarketingCentre {
  background: linear-gradient(30deg, #dd2c00 50%, #ff3d00 100%);
}
.MyIncome {
  background: linear-gradient(30deg, #43a047 50%, #66bb6a 100%);
}
.ShopSettings {
  background: linear-gradient(30deg, #757575 50%, #bdbdbd 100%);
}
::v-deep .v-slide-group__content {
  justify-content: center;
}
</style>
