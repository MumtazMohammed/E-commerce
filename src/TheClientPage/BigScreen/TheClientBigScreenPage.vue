<template>
  <v-main class="grey lighten-3">
    <SystemBar />
    <v-container fluid style="overflow: hidden">
      <v-row>
        <v-card flat tile color="transparent">
          <v-navigation-drawer
            v-model="drawer"
            :mini-variant.sync="mini"
            permanent
          >
            <v-list-item class="px-2">
              <v-list-item-avatar>
                <v-img
                  src="https://randomuser.me/api/portraits/men/85.jpg"
                ></v-img>
              </v-list-item-avatar>

              <v-list-item-title>John Leider</v-list-item-title>

              <v-btn icon @click.stop="mini = !mini">
                <v-icon>mdi-chevron-left</v-icon>
              </v-btn>
            </v-list-item>

            <v-divider></v-divider>

            <v-list color="transparent">
              <v-list-item
                link
                router
                :to="{
                  name: 'UserProfileEdit',
                  params: { Acount: 'حسابي' },
                }"
                exact-path
              >
                <v-icon right class="link-icon"> mdi-account-outline </v-icon>
                <v-list-item-content>
                  <v-list-item-title class="link"> حسابي </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
              <v-list-item
                link
                router
                :to="{
                  name: 'TheClientCartPage',
                  params: { SavedAd: 'سلة التسوق ' },
                }"
                exact-path
              >
                <v-icon right class="link-icon"> mdi-cart-plus </v-icon>
                <v-list-item-content>
                  <v-list-item-title class="link">
                    سلة التسوق
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
              <v-list-item
                link
                exact-path
                router
                :to="{
                  name: 'TheClientOrderPage',
                  params: { MyAdd: 'مشترياتي' },
                }"
              >
                <v-icon right class="link-icon">
                  mdi-ticket-confirmation-outline
                </v-icon>
                <v-list-item-content>
                  <v-list-item-title class="link"> مشترياتي </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
              <v-list-item
                link
                router
                :to="{
                  name: 'ClientNotification',
                  params: { Acount: 'الأشعارات' },
                }"
                exact-path
              >
                <v-icon right class="link-icon"> mdi-bell-outline </v-icon>
                <v-list-item-content>
                  <v-list-item-title class="link">
                    الأشعارات
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
              <v-list-item
                link
                router
                :to="{
                  name: 'TheClientPointsPage',
                  params: { Acount: 'نقاطي' },
                }"
                exact-path
              >
                <v-icon right class="link-icon">
                  mdi-plus-circle-multiple-outline
                </v-icon>
                <v-list-item-content>
                  <v-list-item-title class="link"> نقاطي </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
              <v-list-item
                link
                router
                :to="{
                  name: 'Share',
                  params: { Share: 'شارك وأربح' },
                }"
                exact-path
              >
                <v-icon right class="link-icon"> mdi-party-popper </v-icon>
                <v-list-item-content>
                  <v-list-item-title class="link">
                    شارك وأحصل على 26 نقطة
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
              <v-list-item
                link
                router
                :to="{
                  name: 'TheClientPointsPage',
                  params: { Acount: 'نقاطي' },
                }"
                exact-path
              >
                <v-icon right class="link-icon"> mdi-logout </v-icon>
                <v-list-item-content>
                  <v-list-item-title class="link">
                    تسجيل خروج
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-list>
          </v-navigation-drawer>
        </v-card>
        <v-col class="pa-0 pr-2">
          <v-sheet min-height="40vh" rounded="md">
            <router-view />
          </v-sheet>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>
<script>
import SystemBar from "@/Login/SystemBar.vue";
export default {
  name: "NormalUserPage",
  components: { SystemBar },
  // components: { NavigationUser },
  data() {
    return {
      drawer: true,
      items: [
        { title: "Home", icon: "mdi-home-city" },
        { title: "My Account", icon: "mdi-account" },
        { title: "Users", icon: "mdi-account-group-outline" },
      ],
      mini: true,
    };
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
#inspire {
  width: 100%;
  min-height: 40vh !important;
  background-color: #eeeeee;
  @media (max-width: 600px) {
    padding-bottom: 46px;
  }
  .main {
    min-height: 40vh !important;
  }

  .singout {
    text-decoration: none;
    font-size: 13px;
    font-family: $fontfamliy3 !important;
    font-weight: 500;
    color: $fontcolorlinks;
  }
  .link {
    font-size: 14px;
    font-family: $fontfamliy3 !important;
    font-weight: 600;
    color: $fontcolorlinks;
  }
  .link-icon {
    font-size: 19px;
    color: $color-2;
  }

  ::v-deep a.v-list-item.v-list-item--link.theme--light:not(:last-child) {
    border-bottom: 0.5px solid rgb(212, 212, 212);
  }
  .icon {
    color: $color-2;
  }
}
::v-deep
  nav.px-0.v-navigation-drawer.v-navigation-drawer--fixed.v-navigation-drawer--is-mobile.v-navigation-drawer--open.v-navigation-drawer--right.theme--light {
  z-index: 208;
}
::v-deep.v-overlay.v-overlay--active.theme--dark {
  z-index: 208;
}
::v-deep .v-toolbar__content {
  align-items: flex-start;
  // justify-content: end;
}
</style>
