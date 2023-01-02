<template>
  <div class="Shape_box hidden-sm-and-up">
    <v-container>
      <v-card rounded="" flat color="#eee" class="pa-2">
        <v-row no-gutters>
          <v-col cols="5" style="position: relative">
            <v-row align="center" no-gutters>
              <v-icon right color="primary" size="20">
                mdi-wallet-outline
              </v-icon>
              <v-card-subtitle class="text pa-0"> المحفظة </v-card-subtitle>
            </v-row>
          </v-col>
          <v-col cols="3" style="position: relative">
            <v-card-subtitle class="text pa-0">
              نقاط
              <span class="icon mr-2"> 34 </span>
            </v-card-subtitle>
          </v-col>
          <v-col cols="1" style="position: relative">
            <v-divider vertical class="primary"> </v-divider>
          </v-col>

          <v-col cols="3" style="overflow: hidden">
            <v-card-subtitle class="text pa-0">
              قسائم
              <small class="icon mr-2"> 480 </small>
            </v-card-subtitle>
          </v-col>
        </v-row>
      </v-card>
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
    color: $fontcolorlinks;
    font-weight: 600;
    // text-align: center;
  }
}

.icon {
  // position: absolute !important;
  // margin: 0 auto !important;/
  // background-color: #eee;
  // box-shadow: 0 0 0 4px $color-background !important;
  // border-radius: 50% !important;
  // color: $color-2 !important;
  // width: 33px;
  // height: 33px;
  // display: flex;
  // align-items: center;
  // justify-content: center;
  font-size: 13.5px !important;
  letter-spacing: 1.5px;
  color: $color-2;

  // display: block;
  // text-align: center;
}
</style>
