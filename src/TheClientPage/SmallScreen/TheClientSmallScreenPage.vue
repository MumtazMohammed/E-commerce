<template>
  <div class="inspire pb-2">
    <v-toolbar height="170px" dense tile flat>
      <v-card flat tile class="pt-2 pr-2" color="#eee" width="100%">
        <v-card-actions class="pa-0" style="">
          <!-- cart shopping  -->
          <v-badge bordered overlap content="534" class="mx-1">
            <v-btn
              :to="{
                name: 'SmallScreenClientCartPage',
                params: { Cart: 'سلةالتسوق' },
              }"
              depressed
              class="btn-noti-cart"
              icon
            >
              <v-icon size="20" class="btn-noti-cart-icon"
                >mdi-cart-outline</v-icon
              >
            </v-btn>
          </v-badge>
          <!-- notification btn -->
          <v-badge bordered overlap content="20" class="mx-1">
            <v-btn
              :to="{
                name: 'SmallScreenNotification',
                params: { Notfication: 'الأشعارات' },
              }"
              exact-path
              depressed
              class="btn-noti-cart"
              icon
            >
              <v-icon size="20" class="btn-noti-cart-icon"
                >mdi-bell-outline</v-icon
              >
            </v-btn>
          </v-badge>
          <v-spacer></v-spacer>
          <v-btn
            :to="{
              name: 'SmallScreenUserProfileEdit',
              params: { Profile: 'الملف الشخصي' },
            }"
            depressed
            class="btn-noti-cart"
            icon
          >
            <v-icon size="20" class="btn-noti-cart-icon">mdi-cog</v-icon>
          </v-btn>
        </v-card-actions>
      </v-card>
      <v-spacer></v-spacer>
      <v-avatar size="55" color="grey">
        <!-- <img src="src" alt="alt" /> -->
      </v-avatar>
      <span class="user-username">الحريبي</span>
    </v-toolbar>
    <v-card color="#fff" tile elevation="0" class="mx-auto mt-2 py-2">
      <v-card-actions class="justify-space-around align-center pa-0">
        <v-card
          :to="{
            name: 'SmallScreenClientCartPage',
            params: { Cart: 'سلةالتسوق' },
          }"
          tile
          flat
          color="transparent"
          class="link-small-screen"
        >
          <v-icon class="link-icon-small"> mdi-cart-plus </v-icon>
          <span> سلة التسوق </span>
        </v-card>
        <v-card
          flat
          tile
          :to="{
            name: 'SmallScreenClientOrderPage',
            params: { Order: 'سلةالتسوق' },
          }"
          color="transparent"
          class="link-small-screen"
        >
          <v-icon class="link-icon-small">
            mdi-ticket-confirmation-outline
          </v-icon>
          <span>مشترياتي</span>
        </v-card>
        <v-card
          flat
          router
          :to="{
            name: 'SmallScreenClientPointsPage',
            params: { Points: 'نقاطي' },
          }"
          exact-path
          color="transparent"
          class="link-small-screen"
        >
          <v-icon class="link-icon-small">
            mdi-plus-circle-multiple-outline
          </v-icon>
          <span>نقاطي</span>
        </v-card>
        <v-card
          :to="{
            name: 'SmallScreenNotification',
            params: { Notfication: 'الأشعارات' },
          }"
          flat
          tile
          color="transparent"
          class="link-small-screen"
        >
          <v-icon class="link-icon-small"> mdi-bell-outline </v-icon>
          <span>الأشعارات</span>
        </v-card>
      </v-card-actions>
    </v-card>
    <!-- <LastviewedSmallScreen /> -->
    <v-sheet class="mt-2 mx-auto">
      <v-card
        tile
        flat
        class="start-selling-text"
        :to="{
          name: 'SmallScreenClientRating',
          params: { Rating: 'تقييماتي' },
        }"
      >
        <v-card-title class="pa-2 start-selling-text">
          <v-icon right>mdi-star-outline </v-icon>
          التقيمات
          <v-spacer></v-spacer>
          <v-icon>mdi-chevron-left</v-icon>
        </v-card-title>
      </v-card>
      <v-card
        tile
        flat
        class="start-selling-text"
        :to="{
          name: 'LastviewedSmallScreen',
          params: { Profile: 'الملف الشخصي' },
        }"
      >
        <v-card-title class="pa-2 start-selling-text">
          <v-icon right>mdi-star-outline </v-icon>
          شوهدت مؤخرا
          <v-spacer></v-spacer>
          <v-icon>mdi-chevron-left</v-icon>
        </v-card-title>
      </v-card>
      <v-card
        tile
        flat
        class="start-selling-text"
        :to="{
          name: 'SmallScreenShare',
          params: { Share: 'شارك وأحصل على 26 نقطة' },
        }"
      >
        <v-card-title class="pa-2 start-selling-text">
          <v-icon right>mdi-star-outline </v-icon>
          شارك وأحصل على 26 نقطة
          <v-spacer></v-spacer>
          <v-icon>mdi-chevron-left</v-icon>
        </v-card-title>
      </v-card>
    </v-sheet>
    <v-sheet class="mt-2 mx-auto">
      <v-card
        tile
        flat
        class="start-selling-text"
        :to="{
          name: 'SmallScreenUserProfileEdit',
          params: { Profile: 'الملف الشخصي' },
        }"
      >
        <v-card-title class="pa-2 start-selling-text">
          <v-icon right>mdi-account-cog-outline</v-icon>
          إعدادات الحساب
          <v-spacer></v-spacer>
          <v-icon>mdi-chevron-left</v-icon>
        </v-card-title>
      </v-card>

      <v-card-title class="pa-2 start-selling-text">
        <v-icon right>mdi-help-circle-outline</v-icon>
        المساعدة
        <v-spacer></v-spacer>
        <v-icon>mdi-chevron-left</v-icon>
      </v-card-title>
      <v-card-title class="pa-2 start-selling-text">
        <v-icon right>mdi-headphones-settings </v-icon>
        تواصل معنا
        <v-spacer></v-spacer>
        <v-icon>mdi-chevron-left</v-icon>
      </v-card-title>
      <v-card-title class="pa-2 start-selling-text">
        <v-icon right>mdi-book-alert</v-icon>
        السياسة والخصوصية
        <v-spacer></v-spacer>
        <v-icon>mdi-chevron-left</v-icon>
      </v-card-title>
      <v-card-title class="pa-2 start-selling-text">
        <v-icon right>mdi-logout-variant</v-icon>
        تسجيل الخروج
        <v-spacer></v-spacer>
        <v-icon>mdi-chevron-left</v-icon>
      </v-card-title>
      <v-card-title dark class="pa-2 start-selling-text">
        <v-icon right>mdi-cash-plus</v-icon>
        ابدأ البيع
        <v-spacer></v-spacer>
        <v-icon>mdi-chevron-left</v-icon>
      </v-card-title>
    </v-sheet>
  </div>
</template>
<script>
// import LastviewedSmallScreen from "./LastviewedSmallScreen.vue";
export default {
  name: "TheClientSmallScreenPage",
  // components: { LastviewedSmallScreen },
  // components: { NavigationUser },
  data() {
    return {
      drawer: false,
    };
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";

.inspire {
  min-height: 94vh;
  @media (max-width: 600px) {
    margin-bottom: 50px;
  }
}
.link-icon-small {
  font-size: 19px !important;
  color: $color-2 !important;
}
.link-small-screen {
  font-size: 19px;
  border-radius: 5px;
  flex-basis: auto !important;
  // border: 2px solid $color-2 !important;
  // height: 60px;
  display: flex;
  justify-content: start;
  flex-direction: column;
  // align-items: flex-end;
  span {
    font-size: 12px;
    margin-top: 10px;
    font-family: $fontfamliy2 !important;
    font-weight: 600;
    text-align: center;
    letter-spacing: 0 !important;
    color: $fontcolorlinks;
  }
}
.user-username {
  font-size: 14px;
  margin: 10px 0;
  font-family: $fontfamliy3 !important;
  font-weight: 600;
  text-align: center;
  letter-spacing: 0 !important;
  color: $fontcolorlinks;
}
.toolbar-icon {
  color: $color-2 !important;
  font-size: 20px !important;
}
.start-selling-text {
  font-size: 13px;
  font-family: $fontfamliy3 !important;
  font-weight: 600;
  letter-spacing: 0px !important;
  color: $fontcolorlinks;
  .v-icon:not(:first-child) {
    color: $color-2;
  }
  .v-icon:not(:last-child) {
    color: #fc624ddb;
    font-size: 18px;
  }
}

.start-selling-text:not(:last-child) {
  border-bottom: 1px solid rgb(213, 213, 213) !important;
}
::v-deep a.v-list-item.v-list-item--link.theme--light:not(:last-child) {
  border-bottom: 0.5px solid rgb(212, 212, 212);
}
::v-deep .v-toolbar__content {
  flex-direction: column;
  padding: 0px;
}
.icon {
  color: $color-2;
}
::v-deep span.v-badge__badge {
  color: rgb(255, 255, 255) !important;
  // font-weight: 500;
  background-color: $color-2 !important;
  min-width: 15px;
  height: 15px;
  padding: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
  border: none;
  inset: auto calc(100% - 50px) calc(100% - 16px) auto !important;
}
::v-deep .theme--light.v-badge .v-badge__badge:after {
  border-width: 0.2px;
}
.btn-noti-cart-icon {
  color: $color-2 !important;
}
</style>
