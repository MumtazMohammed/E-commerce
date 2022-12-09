<template>
  <div class="TheShowRoomPage">
    <v-container class="container">
      <v-row no-gutters>
        <v-col cols="12" class="">
          <v-sheet rounded="lg" max-height="500" class="pa-3">
            <v-card-title class="text py-1 grey--text text--darken-2">
              <v-icon color="green lighten-2" right
                >mdi-bullhorn-outline</v-icon
              >
              إعلان
            </v-card-title>
            <v-row no-gutters>
              <v-col cols="12" class="pa-2" sm="6" md="4" lg="4">
                <v-card
                  min-height="100%"
                  class="overflow-hidden pb-2"
                  color="#fff"
                  rounded="lg"
                >
                  <div>
                    <v-subheader
                      class="Adv-titel pl-0 grey--text text--darken-1"
                    >
                      هل أستطيع التعديل على التنسيقات؟
                      <v-spacer></v-spacer>
                      <v-btn icon>
                        <v-icon size="19" color="red lighten-2">
                          mdi-trash-can
                        </v-icon>
                      </v-btn>
                    </v-subheader>
                    <v-card-text
                      class="Adv-text py-0 grey--text text--darken-1"
                    >
                      بلا شك، يمكنك تغيير النصوص والصور، اختيار ألوانك الخاصة،
                      ترتيب مكونات الصفحة بطريقتك، تغيير تقسيم الأعمدة… وأكثر،
                      كل ذلك بالسحب والإدراج وملء الخانات. ويمكنك أيضاً استخدام
                      التنسيق الواحد في أكثر من صفحة والتعديل عليها حسب ذوقك.
                    </v-card-text>
                  </div>
                </v-card>
              </v-col>
            </v-row>
          </v-sheet>
        </v-col>
        <v-col class="py-2">
          <!-- To Do list  -->
          <v-row no-gutters>
            <v-col
              md="4"
              lg="4"
              sm="6"
              cols="12"
              v-for="(ToDo, i) in ToDoList"
              :key="i"
            >
              <v-card class="ma-1 ToDoList-card">
                <v-card-title class="subtitle">
                  {{ ToDo.ToDoName }}
                  <v-spacer></v-spacer>
                  <span class="blue--text text--darken-1 subtitle">
                    {{ ToDo.ToDoNumber }}
                  </span>
                </v-card-title>
                <v-sheet class="mx-auto" max-width="300">
                  <v-sparkline
                    :value="value"
                    :smooth="9"
                    :padding="3"
                    :line-width="6"
                    stroke-linecap="round"
                    :gradient="['#F4511E', '#FF7043']"
                    type="trend"
                    auto-line-width="true"
                    auto-draw
                    color="grey"
                  >
                  </v-sparkline>
                </v-sheet>
              </v-card>
            </v-col>
          </v-row>
          <v-sheet flat class="mt-4 pa-2 overflow-hidden" rounded="lg">
            <v-card-title
              class="Marketing-text justify-center white grey--text text--accent-3 py-2"
            >
              مركز التسويق والعروض
            </v-card-title>
            <div class="py-3">
              <v-row no-gutters>
                <v-col class="pa1" cols="12" md="6" sm="m" lg="6">
                  <v-card max-width="100%" class="pa-2">
                    <v-card-title class="text deep-orange--text pa-2 py-0">
                      عروض الجمعة
                      <v-spacer></v-spacer>
                      <v-btn
                        small
                        text
                        class="enter-theOffer px-2"
                        elevation="0"
                        color="green accent-4"
                      >
                        دخول العرض
                        <!-- <v-icon class="white--text">mdi-plus</v-icon> -->
                      </v-btn>
                    </v-card-title>
                    <v-alert
                      border="left"
                      colored-border
                      color="success"
                      elevation="0"
                      class="ma-0 pa0"
                      rounded="0"
                    >
                      <small class="mb-1"> 22 / 05 / 2020 </small>
                      <div class="text-offer">
                        ابتداً من التاريخ الموضح سيتم نشر العروض في الساعة
                        <span class="success--text mr-2">12:00 صباحاً</span>
                      </div>
                    </v-alert>
                    <v-divider inset></v-divider>
                    <v-alert
                      border="left"
                      colored-border
                      color="error"
                      elevation="0"
                      class="ma-0"
                      rounded="0"
                    >
                      <small class="mb-1"> 22 / 05 / 2020 </small>
                      <div class="text-offer">
                        ابتداً من التاريخ الموضح سيتم إغلاق العروض في الساعة
                        <span class="error--text mr-1">12:00 مساً</span>
                      </div>
                    </v-alert>
                  </v-card>
                </v-col>
              </v-row>
            </div>
            <v-card>
              <v-card-title class="Marketing-titel pa-3">
                التسويق
              </v-card-title>
              <v-sheet color="grey lighten-3" class="px-2 mb-5">
                <v-row class="mt-0" fill-height>
                  <v-col cols="12" sm="6" md="6" lg="6">
                    <v-card flat height="200">
                      <v-card-actions class="flex-column pb-0">
                        <v-icon class="icon-Marketing">mdi-star</v-icon>
                        <v-card-text class="text-center title-featur pa-2">
                          المنتجات المتميزة
                        </v-card-text>
                      </v-card-actions>
                      <v-card-text class="text-center text-featur pt-0 pa-2">
                        المنتجات المتميزةالمنتجات المتميزةالمنتجات
                        المتميزةالمنتجات المتميزةالمنتجات المتميزةالمنتجات
                        المتميزةالمنتجات المتميزةالمنتجات المتميزة
                      </v-card-text>
                    </v-card>
                  </v-col>
                  <v-col cols="12" sm="6" md="6" lg="6">
                    <v-card flat height="200">
                      <v-card-actions class="flex-column pb-0">
                        <v-icon class="icon-Marketing">
                          mdi-ticket-percent
                        </v-icon>
                        <v-card-text class="text-center title-featur pa-2">
                          قسائم
                        </v-card-text>
                      </v-card-actions>
                      <v-card-text class="text-center text-featur pt-0 pa-2">
                        قم بزيادة الطلبات من خلال تقديم أسعار مخفضة للمشترين عند
                        الخروج باستخدام القسائم.
                      </v-card-text>
                    </v-card>
                  </v-col>
                </v-row>
              </v-sheet>
            </v-card>
          </v-sheet>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script>
import ShowRoomUserCars from "../data-json/All-Car.json";
// import VueApexCharts from "vue-apexcharts";
export default {
  name: "MainStorePage",
  components: {},
  data() {
    return {
      ToDolist: false,
      BusinessInsights: false,
      search: "",
      ShowRoomUserCars,
      carId: this.$route.params.carId,

      ToDoList: [
        {
          ToDoName: "الطلبات",
          ToDoNumber: 0,
        },
        {
          ToDoName: "الربح ",
          ToDoNumber: 0,
        },
        {
          ToDoName: "الزائرين",
          ToDoNumber: 0,
        },
      ],
      value: [0, 2, 5, 9, 5, 10, 3],
      labels: [
        "السبت",
        "الأحد",
        "الأثنين",
        "الثلاثاء",
        "الأربعاء",
        "الخميس",
        "الجمعة",
      ],
    };
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.TheShowRoomPage {
  width: 100%;
  min-height: 100vh;
  @media (max-width: 600px) {
    margin-bottom: 50px;
  }
  .text {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    font-weight: 500;
    font-size: 17px;
    @media (max-width: 600px) {
      font-size: 15px;
    }
    .v-icon {
      font-size: 18px !important;
    }
  }
  .Adv-titel {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    font-weight: 600;
    font-size: 14px;
  }
  .Adv-text {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    font-weight: 400;
    font-size: 13px;
    line-height: 1.8;
    text-align: justify;
  }
  .text-offer {
    letter-spacing: 0 !important;
    font-family: $fontfamliy3;
    text-align: justify;
    line-height: 1.7;
    font-size: 14px;
    color: $fontcolorlinks;
  }
  .enter-theOffer {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
  }
  .icon-Marketing {
    height: 30px;
    width: 30px;
    background-color: $color-2;
    color: #fff;
    font-size: 23px;
    border-radius: 50%;
  }
  .Marketing-titel {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    justify-content: center;
    color: $color-2;
  }
  .text-featur {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    color: rgb(97, 97, 97) !important;
    line-height: 1.8;
  }
  .title-featur {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    color: rgb(33, 33, 33) !important;
  }
  .Marketing-text {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
  }
  .subtitle {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    font-weight: 600;
    color: $color-2 !important;
    font-size: 17px;
    text-align: center;
    span {
      font-size: 20px;
    }
  }
}
.ToDoList-box {
  @media (max-width: 600px) {
    flex-direction: column;
  }
}
.Store-name {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-weight: 500;
  color: $fontcolorlinks !important;
  text-align: center;
}
::v-deep .v-timeline-item__divider {
  min-width: 50px;
}
::v-deep .v-timeline-item__body {
  max-width: calc(100% - 50px) !important;
}
::v-deep .theme--light.v-timeline:before {
  right: 24px !important;
}

.offers-card::-webkit-scrollbar {
  width: 0.5em;
}

.offers-card::-webkit-scrollbar-track {
  background-color: #eee;
}

.offers-card::-webkit-scrollbar-thumb {
  background-color: darkgrey;
}
</style>
