<template>
  <div class="box">
    <!-- <p class="card_title text-center mb-1">سوق ثــقـة</p> -->
    <!-- <p class="card_title text-center mb-1">
        بيع سيارتك أو اشتري سيارتك على حراج ثقة لسيارات
      </p> -->
    <div class="section">
      <p class="card_text text-center mb-1">عندك بضائع وتحب تشاركها للكل</p>
      <p class="card_text text-center mb-1">كن بائع معنا وابداء الان..</p>
      <!-- <v-btn
        router
        width="100%"
        to="/AboutSellingCarFreeAdd"
        elevation="0"
        color="#fc624d"
        class="btn px-3 mt-3 "
      >
        بفتح مشروعك
      </v-btn> -->
    </div>
    <!-- <div class="advertise">
      <a class="white--text">للأعلان </a>
    </div> -->
  </div>
</template>
<script>
export default {
  name: "ToSellYourCarInfo",
  components: {},
  data() {
    return {
      row: null,
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
    font-size: 18px;
    color: $fontcolorlinks;
    font-family: $fontfamliy2;
    font-weight: 600;

    @media (max-width: 760px) {
      font-size: 17px;
    }
    @media (max-width: 500px) {
      font-size: 15px;
    }
  }

  .theme--light.v-card {
    background-color: rgba(0, 0, 0, 0) !important;
  }
  .btn {
    font-family: $fontfamliy2;
    color: #fff;
    font-size: 16px;
    letter-spacing: 0;
    font-weight: 500;

    @media (max-width: 500px) {
      font-size: 15px;
    }
  }
  .advertise {
    position: absolute;
    bottom: 5px;
    right: 5px;
    @media (max-width: 960px) {
      position: relative;
      bottom: 0px;
      right: 0px;
    }
    a {
      font-family: $fontfamliy;
      font-size: 18px;
      @media (max-width: 960px) {
        color: $color-1 !important;
      }
    }
  }
}
</style>
