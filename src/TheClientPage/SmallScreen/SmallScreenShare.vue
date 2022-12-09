<template>
  <div class="BestOffer">
    <v-app-bar class="mb-5" app>
      <v-toolbar-title class="toolbar-title">
        <v-icon right>mdi-account </v-icon>
        شارك وأحصل على 26 نقطة
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/TheUserPageView" icon>
        <v-icon size="30">mdi-arrow-left-thin</v-icon>
      </v-btn>
    </v-app-bar>
    <v-container class="container py-0 mt-15">
      <v-img
        aspect-ratio="1.7"
        contain
        src="@/assets/outsrc/undraw_happy_birthday_re_c16u.svg"
      ></v-img>
      <div class="py-3 d-flex font-weight-bold tital">
        شارك وأحصل على 26 نقطة عند دعوة أشخاص أخرين
      </div>
      <v-row>
        <v-col cols="12" class="pt-">
          <v-card class="mb-2 overflow-hidden" width="100%">
            <div>
              <span class="span-no">1</span>
            </div>
            <v-card-text class="how-to-use">
              قم بدعوة أشخاص بتسجيل على موقعنا عن طريق الرابط الخاص بك
            </v-card-text>
          </v-card>
          <v-card class="mb-2 overflow-hidden" width="100%">
            <div>
              <span class="span-no">2</span>
            </div>
            <v-card-text class="how-to-use">
              سوف تحصل على نقاطك عندما يتم التسجيل من قبل المستخدم بشكل كامل
            </v-card-text>
          </v-card>
          <v-card class="overflow-hidden" width="100%">
            <div>
              <span class="span-no">3</span>
            </div>
            <v-card-text class="how-to-use">
              قم بتحويل النقاط الى أموال أو بإمكانك الشراء من خلال الموقع
            </v-card-text>
          </v-card>
        </v-col>
        <v-col class="pb-0" cols="12">
          <v-text-field
            hide-details
            dense
            readonly
            rounded
            solo
            flat
            dark
            v-model="link"
          ></v-text-field>
          <v-card-actions class="justify-center py-3">
            <v-btn elevation="0" rounded width="150" class="copy-btn">
              <v-icon right size="20">mdi-content-copy</v-icon>
              نسخ الرابط
            </v-btn>
          </v-card-actions>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "BestOffer",
  components: {},
  data() {
    return {
      link: "http://localhost:8081/SmallScreenShare/%D8%B4%D8%A7%D8%B1%D9%83%2F&%20%D9%88%D8%A3%D8%AD%D8%B5%D9%84%20%D8%B9%D9%84%D9%89%2026%20%D9%86%D9%82%D8%B7%D8%A9",
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
  computed: {
    getCarInfo() {
      let GetCarVerified = [];
      for (let i = 0; i < this.VerifiedCar.length; i++) {
        if (this.VerifiedCar[i].Vip == true) {
          GetCarVerified.push(this.VerifiedCar[i]);
        }
      }
      return GetCarVerified;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.BestOffer {
  width: 100%;
  min-height: calc(100vh - 60px);
  font-family: $fontfamliy;
  padding-bottom: 20px;
  strong {
    color: $color-2;
  }
  .toolbar-title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorlinks !important;
    font-size: 16px !important;
    font-weight: 600;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    .v-icon {
      color: $color-2 !important;
      margin-left: 5px;
    }
  }
  .tital {
    font-family: $fontfamliy3;
    font-size: 14px;
    color: $fontcolorlinks;
    margin-top: 15px;
    justify-content: center;
    letter-spacing: 0px !important;

    @media (max-width: 350px) {
      font-size: 14px;
    }
  }
  a {
    font-size: 13px;
  }
  .copy-btn {
    font-family: $fontfamliy3;
    font-size: 14px;
    color: $color-2;
    letter-spacing: 0px !important;
    background-color: #eee !important;
  }
  .how-to-use {
    font-family: $fontfamliy3;
    font-size: 14px;
    color: $fontcolorlinks;
    letter-spacing: 0px !important;
    line-height: 1.6;
    text-align: justify;
    padding-top: 0px !important;
  }
}
::v-deep .theme--dark.v-text-field--solo > .v-input__control > .v-input__slot {
  background: $color-2 !important;
}
.span-no {
  width: 30px;
  height: 30px;
  background-color: $color-2;
  display: block;
  text-align: center;
  clip-path: circle(100% at 100% 0);
  color: #fff;
}
</style>
