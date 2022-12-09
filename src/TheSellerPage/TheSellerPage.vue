<template>
  <div class="TheShowRoomPage grey lighten-3">
    <ShowRoomBtnsNavgition />
    <div class="router">
      <router-view> </router-view>
    </div>
    <!-- bottom navigation for seller -->
    <div class="hidden-sm-and-up">
      <v-bottom-navigation
        :class="active ? 'nav-top' : ''"
        height="50"
        class="first-nav elevation-0"
        background-color="white"
        active-class="blue--text"
        light
        flat
        fixed
        grow
      >
        <v-btn to="/">
          <span class="text">الرئيسية</span>
          <v-icon>mdi-home-variant </v-icon>
        </v-btn>

        <v-btn to="/Login">
          <span class="text">حسابي</span>
          <v-icon>mdi-account-outline </v-icon>
        </v-btn>

        <v-btn to="/TheUserPageView">
          <span class="text">البحث</span>
          <v-icon>mdi-magnify </v-icon>
        </v-btn>
        <v-btn v-if="!active" @click="active = !active">
          <span class="text">المزيد</span>
          <v-icon>mdi-chevron-down </v-icon>
        </v-btn>
        <v-btn v-else @click="active = !active">
          <span class="text">رجوع</span>
          <v-icon>mdi-chevron-up </v-icon>
        </v-btn>
      </v-bottom-navigation>
      <v-bottom-navigation
        height="50"
        background-color="white"
        active-class="blue--text"
        class="elevation-0"
        light
        flat
        fixed
        grow
      >
        <!-- <v-btn to="/">
        <span class="text">الرئيسية</span>
        <v-icon>mdi-home-variant </v-icon>
      </v-btn> -->

        <v-btn to="/Login">
          <span class="text">حسابي</span>
          <v-icon>mdi-account-outline </v-icon>
        </v-btn>

        <v-btn to="/TheUserPageView">
          <span class="text">البحث</span>
          <v-icon>mdi-magnify </v-icon>
        </v-btn>

        <v-btn to="/TheShowRoomPage">
          <span class="text">الإشعارات</span>
          <v-icon>mdi-bell-outline </v-icon>
        </v-btn>
      </v-bottom-navigation>
    </div>
  </div>
</template>
<script>
// import Cars from "./ShowRoomCars.vue";
// import Info from "./ShowRoomCarsInfo.vue";
import ShowRoomBtnsNavgition from "./StoreNavigation.vue";
export default {
  name: "TheShowRoomPage",
  components: { ShowRoomBtnsNavgition },
  data() {
    return {
      active: false,

      search: "",
    };
  },
  computed: {
    filteredStore: function () {
      return this.showrooms.filter((showroom) => {
        return showroom.ShowroomName.match(this.search);
      });
    },
    items() {
      return Array.from({ length: this.length }, (k, v) => v + 1);
    },
    length() {
      return 7000;
    },
  },
  methods: {
    reset() {
      return (this.search = "");
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.TheShowRoomPage {
  width: 100%;
  min-height: 70vh;
  // background-color: $backgroundcard;

  .router {
    @media (max-width: 600px) {
      // padding: 15px;
    }
  }
}
.text {
  font-family: $fontfamliy2 !important;
  letter-spacing: 0 !important;
  margin-top: 5px;
}
::v-deep
  .v-bottom-navigation.first-nav.v-item-group.theme--light.v-bottom-navigation--fixed.white {
  z-index: 12 !important;
}
::v-deep .v-item-group.v-bottom-navigation--fixed {
  z-index: 11 !important;
}
.first-nav {
  z-index: 13 !important;
}
.nav-top {
  bottom: 49.5px !important;
}
</style>
