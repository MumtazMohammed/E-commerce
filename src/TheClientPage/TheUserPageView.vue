<template>
  <v-app id="inspire">
    <TheUserPageBigScreen class="hidden-xs-only" />
    <TheUserPageSmallScreen class="hidden-sm-and-up" />
    <FixedBottomNav class="hidden-sm-and-up" />
  </v-app>
</template>
<script>
import TheUserPageSmallScreen from "./SmallScreen/TheClientSmallScreenPage.vue";
import TheUserPageBigScreen from "./BigScreen/TheClientBigScreenPage.vue";
import FixedBottomNav from "../NavBar/FixedBottomNav.vue";
export default {
  name: "TheUserPageView",
  components: { TheUserPageBigScreen, TheUserPageSmallScreen, FixedBottomNav },
  // components: { NavigationUser },
  data() {
    return {
      drawer: false,
    };
  },
};
</script>
<style lang="scss" scoped>
@import "../scss/virables";
@import "../scss/mixin";
#inspire {
  width: 100%;
  min-height: 80vh;
  background-color: #eee;
}
</style>
