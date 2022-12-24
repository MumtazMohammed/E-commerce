<template>
  <div class="Shape_box">
    <v-container>
      <v-row no-gutters>
        <v-col cols="6" class="pa-1" style="position: relative">
          <v-card rounded="lg" flat color="#eee">
            <v-card-text class="text pa-1 pb-0">نقاط</v-card-text>
            <span class="Number pa-1 pt-0"> 0 </span>
          </v-card>
        </v-col>
        <v-col cols="6" class="pa-1" style="position: relative">
          <v-card rounded="lg" flat color="#eee">
            <v-card-text class="text pa-1 pb-0">قسائم</v-card-text>
            <span class="Number pa-1 pt-0"> 0 </span>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "CarShape",
  components: {},
  data() {
    return {};
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";

.Shape_box {
  background-color: #f8f9fa;

  .text {
    font-family: $fontfamliy3 !important;
    font-size: 14px !important;
    letter-spacing: 0 !important;
    justify-content: space-evenly;
    color: $fontcolorlinks;
    font-weight: 600;
    text-align: center;
  }
  .Number {
    color: $color-2 !important;
    display: block;
    text-align: center;
    font-size: 16px !important;
    font-weight: 600;
  }
}

.info-icon {
  color: $color-2 !important;
}
</style>
