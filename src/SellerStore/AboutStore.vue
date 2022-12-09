<template>
  <div class="AboutStore">
    <v-card-title class="py-0 titel"> عن المتجر </v-card-title>
    <v-row>
      <v-col cols="12" md="6" sm="6">
        <v-card-text class="pa-2 text">
          حيث يحتاج العميل فى كثير من الأحيان أن يطلع على صورة حقيقية لتصميم
          الموقع. ومن هنا وجب على المصمم أن يضع نصوصا مؤقتة على التصميم ليظهر
          للعميل الشكل كاملاً،دور مولد النص العربى أن يوفر على المصمم عناء البحث
          عن نص بديل لا علاقة له بالموضوع الذى يتحدث عنه التصميم فيظهر بشكل لا
          يليق.
        </v-card-text>
      </v-col>
      <v-col>
        <v-sheet color="grey lighten-3" height="100%" tile>
          <v-row
            no-gutters
            style="justify-content: space-evenly"
            class="fill-height"
            align="center"
          >
            <v-col class="pa-1" cols="6" v-for="i in 6" :key="i">
              <v-img
                src="https://picsum.photos/510/300?random"
                aspect-ratio="1.7"
              ></v-img>
            </v-col>
          </v-row>
        </v-sheet>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import Services from "../data-json/showroom.json";
export default {
  name: "ServicesPage",
  components: {},
  data() {
    return {
      Services,
      model: null,
      filterdialog: null,
      items: ["مقديشو", "كزبرا", "صلصة", "ثوم"],
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
  // computed: {
  //   getCarInfo() {
  //     let GetShowroomfeatured = [];
  //     for (let i = 0; i < this.featuredshowrooms.length; i++) {
  //       if (this.featuredshowrooms[i].featured == true) {
  //         GetShowroomfeatured.push(this.featuredshowrooms[i]);
  //       }
  //     }
  //     return GetShowroomfeatured;
  //   },
  // },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.AboutStore {
  padding: 10px 0;
  background-color: $color-background !important;

  .titel {
    letter-spacing: 0 !important;
    font-size: 17px !important;
    font-weight: 500 !important;
    font-family: $fontfamliy3 !important;
    color: $fontcolor !important;
  }
  .text {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorlinks !important;
    text-align: justify;
    line-height: 1.7;
  }
}
</style>
