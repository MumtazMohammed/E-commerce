<template>
  <div class="Shape_box hidden-sm-and-up">
    <v-container>
      <v-card rounded="lg" flat color="#eee" class="pa-1 text">
        <v-row no-gutters>
          <v-col cols="4" class="pa-1" style="position: relative">
            <v-row no-gutters align="center" justify="center">
              <v-chip
                small
                color="green darken-1"
                text-color="white"
                class="mx-1"
              >
                <v-icon small left>mdi-headphones-settings</v-icon>
                <span> مساعدة </span>
              </v-chip>
            </v-row>
          </v-col>
          <v-col class="pa-1" cols="4" style="position: relative">
            <v-row no-gutters align="center" justify="center">
              <v-chip small color="light-blue darken-1" text-color="white">
                <span> نقاط </span>
                <span class="mr-2"> 425 </span>
              </v-chip>
            </v-row>
          </v-col>

          <v-col class="pa-1" cols="4" style="overflow: hidden">
            <v-row no-gutters align="center" justify="center">
              <v-chip small color="light-blue darken-1" text-color="white">
                <span> قسائم </span>
                <span class="mr-2"> 425 </span>
              </v-chip>
            </v-row>
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
    color: $fontcolor;
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
