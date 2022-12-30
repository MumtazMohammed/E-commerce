<template>
  <div class="Shape_box hidden-sm-and-up">
    <v-container>
      <v-card flat color="#eee">
        <v-row no-gutters>
          <v-col cols="6" style="position: relative">
            <v-card flat tile color="transparent">
              <v-card-text class="text pa-1"> نقاط </v-card-text>
              <span class="icon"> 34 </span>
              <!-- <v-icon class="icon" size="17">mdi-cash-plus</v-icon> -->
            </v-card>
          </v-col>
          <v-col cols="6" style="overflow: hidden">
            <v-card flat tile color="transparent">
              <v-card-text class="text pa-1">قسائم</v-card-text>
              <span class="icon"> 480 </span>
              <!-- <v-icon class="icon" size="17">mdi-ticket-percent</v-icon> -->
            </v-card>
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
    font-size: 13px !important;
    letter-spacing: 0 !important;
    color: #757575;
    font-weight: 600;
    text-align: center;
  }
  .Number {
    color: $color-2 !important;
    display: block;
    text-align: center;
    font-size: 15px !important;
    font-weight: 600;
  }
}

.icon {
  // position: absolute !important;
  margin: 0 auto !important;
  background-color: #eee;
  box-shadow: 0 0 0 4px $color-background !important;
  border-radius: 50% !important;
  color: $color-2 !important;
  width: 33px;
  height: 33px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px !important;
  font-weight: 600;
}
</style>
