<template>
  <v-app class="bind-class-padding">
    <v-main style="min-height: 75vh !important">
      <router-view />
    </v-main>
    <v-btn
      ref="button"
      icon
      elevation="0"
      x-large
      class="btn-up"
      color="white"
      v-bind:class="{
        'btn-up': scrollPosition < 600,
        'is-hidden': scrollPosition > 600,
      }"
      @click="$vuetify.goTo(target, options)"
    >
      <v-icon class="btn-up-icon">fas fa-angle-up</v-icon>
    </v-btn>
    <!-- <IconSearch /> -->
    <Footer class="hidden-xs-only" />
  </v-app>
</template>

<script>
import Footer from "./footer/footer.vue";
export default {
  name: "App",
  components: {
    Footer,
  },
  data() {
    return {
      drawer: false,
      type: "number",
      number: 0,
      duration: 300,
      offset: 0,
      scrollPosition: null,
    };
  },
  mounted() {
    window.addEventListener("scroll", this.updateScroll);
  },
  methods: {
    updateScroll() {
      this.scrollPosition = window.scrollY;
    },
  },
  computed: {
    target() {
      const value = this[this.type];
      if (!isNaN(value)) return Number(value);
      else return value;
    },
    options() {
      return {
        duration: this.duration,
        offset: this.offset,
      };
    },
  },
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;800;900&display=swap");
@import "./scss/virables";
#app {
  background: white;
  width: 100%;
  position: relative;
  overflow: hidden;
}
.bind-class-padding {
  @media (max-width: 600px) {
    // margin-bottom: 50px;
  }
}
.v-main {
  padding: 0px !important;
}
::v-deep .v-application--wrap {
  min-height: 94vh !important;
}
.btn-up {
  position: fixed;
  bottom: -100px;
  right: 8px;
  overflow: hidden;
  z-index: 5000;
  background: $color-2;
  transition: all 0.4s 0s linear !important;
  // opacity: 0;
  pointer-events: none;
  @media (max-width: 600px) {
    bottom: -100px;
    transform: scale(0.8);
    z-index: 1;
  }
  .btn-up-icon {
    font-size: 18px !important;
    transition: all 0.4s 0s linear !important;
    position: relative;
    // z-index: ;
  }
}
.is-hidden {
  z-index: 5000;

  bottom: 40px;
  pointer-events: auto;
  @media (max-width: 600px) {
    bottom: 46px;
  }
}
</style>
