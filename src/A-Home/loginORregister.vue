<template>
  <div class="box">
    <v-icon class="icon">mdi-account</v-icon>
    <p class="card_text my-3 text-center">مرحباً بك في سوق ثقة</p>
    <v-btn
      to="/Login"
      elevation="0"
      width="130px"
      height="36px"
      color="#fc624d"
      class="btn pa-3 ma-0"
    >
      دخول
    </v-btn>
  </div>
</template>
<script>
export default {
  name: "Login",
  components: {},
  data() {
    return {
      dialog: false,
      firstname: "",
      SignUpNormalAccount: false,
      SignUpSellerAccount: false,
      rules: {
        required: (value) => !!value || "ادخل الرقم السري",
        min: (v) => v.length >= 8 || "تأكد من ادخال الرقم صحيحا",
      },
    };
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";

.box {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  width: 100%;
  position: relative;
  @media (max-width: 960px) {
    background: none;
  }
  .card_text {
    font-size: 15px;
    color: $fontcolor;
    font-family: $fontfamliy2;
    @media (max-width: 960px) {
      color: $fontcolor;
    }
    @media (max-width: 760px) {
      font-size: 15px;
    }
    @media (max-width: 500px) {
      font-size: 15px;
      margin: 5px 0 !important;
    }

    @media (max-width: 360px) {
      font-size: 18px;
    }
  }

  .btn {
    font-family: $fontfamliy2;
    color: $fontcolorsm;
    font-size: 13px;
    letter-spacing: 0;
    font-weight: bold;
  }
}
.icon {
  font-size: 50px !important;
  color: #bdbdbd !important;
}
.card-text {
  font-size: 15px;
  color: $color-2;
  font-family: $fontfamliy2;
  @media (max-width: 960px) {
    color: $fontcolor;
  }
  @media (max-width: 760px) {
    font-size: 15px;
  }
  @media (max-width: 500px) {
    font-size: 15px;
    margin: 5px 0 !important;
  }

  @media (max-width: 360px) {
    font-size: 18px;
  }
}
//
</style>
