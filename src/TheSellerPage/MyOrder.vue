<template>
  <div class="UserAdd">
    <v-container class="container">
      <!-- big Screen Tabs  -->
      <v-tabs
        slider-size="2"
        slider-color="#fc624d"
        v-model="tab"
        class="rounded-sm overflow-hidden hidden-xs-only"
        rounded="dm"
        grow
        background-color=""
      >
        <v-tab href="#tab-1" active-class="links-active" class="links">
          الطلبات
        </v-tab>
        <v-tab href="#tab-2" active-class="links-active" class="links">
          بإنتظار شحن المنتج
        </v-tab>
        <v-tab href="#tab-4" active-class="links-active" class="links">
          الطلبات المشحونة
        </v-tab>
      </v-tabs>
      <v-card flat tile min-height="100%" color="" class="">
        <v-tabs-items v-model="tab" class="pa-0 transparent">
          <!-- shipping order  -->
          <v-tab-item value="tab-1">
            <v-row no-gutters>
              <v-col
                v-for="i in 3"
                :key="i"
                cols="12"
                md="4"
                sm="6"
                lg="4"
                class="pa-2 pa-0"
              >
                <v-card width="100%" class="overflow-y-auto overflow-x-hidden">
                  <v-card-title class="title pa-2">
                    طلب جديد
                    <v-spacer></v-spacer>
                    <span> 25 / 2 /2022 </span>
                  </v-card-title>
                  <v-card-title
                    class="pa-2 client-Info"
                    v-for="item in CustomerInfo"
                    :key="item.name"
                  >
                    <span> {{ item.name }} </span>
                    <v-spacer></v-spacer>
                    {{ item.calories }}

                    <v-chip
                      v-for="(date, i) in item.DateTime"
                      :key="i"
                      color="grey"
                      class="px-0 ma-1 text-truncate"
                      dark
                      small
                      style="max-width: 160px"
                    >
                      <v-card-text class="text-truncate pa-0 px-2 PerPrder">
                        {{ date }}
                      </v-card-text>
                    </v-chip>
                  </v-card-title>

                  <v-card-actions class="justify-center">
                    <v-btn text width="180" class="btn2"> رؤية الطلب </v-btn>
                  </v-card-actions>
                </v-card>
              </v-col>
            </v-row>
          </v-tab-item>
          <!-- Confirm for shipping -->
          <v-tab-item value="tab-2">
            <v-col v-for="i in 2" :key="i" cols="12" class="py-2 pa-0">
              <v-card
                width="100%"
                min-height="300"
                max-height="390"
                v-scroll.self="onScroll"
                class="overflow-y-auto overflow-x-hidden pa-1"
                color=""
              >
                <span class="title pa-0 pr-2 grey--text text--darken-2"
                  >معلومات الشحن
                </span>
                <v-simple-table class="rounded-0" dense>
                  <template v-slot:default>
                    <tbody>
                      <tr v-for="item in CustomerInfo" :key="item.name">
                        <td class="client-Info">{{ item.name }}</td>
                        <td class="client-Info">{{ item.calories }}</td>
                      </tr>
                      <tr v-for="item in ShipmentInfo" :key="item.name">
                        <td class="client-Info">{{ item.name }}</td>
                        <td class="client-Info pb-1">
                          <v-text-field
                            dense
                            placeholder="أدخل المعلومات"
                            class="pt-0 ma-0"
                            hide-details=""
                          ></v-text-field>
                        </td>
                      </tr>
                    </tbody>
                  </template>
                </v-simple-table>
                <v-card-actions class="justify-center">
                  <v-btn outlined class="btn2">تأكيد الطلب</v-btn>
                  <v-btn outlined class="btn2"> إلغاء الطلب</v-btn>
                  <v-btn outlined class="btn2"> مراسلة العميل</v-btn>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-tab-item>
          <!-- Cancelled Products -->
          <v-tab-item value="tab-4">
            <v-col v-for="i in 2" :key="i" cols="12" class="py-2 pa-0">
              <v-card
                width="100%"
                min-height="250"
                max-height="300"
                v-scroll.self="onScroll"
                class="overflow-y-auto overflow-x-hidden"
                color=""
              >
                <v-card-actions class="pa-0">
                  <v-btn class="client-Info" small elevation="0" tile>
                    حذف
                  </v-btn>
                  <v-btn class="client-Info" small elevation="0" tile>
                    طباعة
                  </v-btn>
                  <v-spacer></v-spacer>
                  <span class="client-Info pl-3">15 / 10 / 2020</span>
                </v-card-actions>
                <span class="title pa-0 pr-2 grey--text text--darken-2"> </span>
                <v-simple-table class="rounded-0" dense>
                  <template v-slot:default>
                    <tbody>
                      <tr>
                        <td class="client-Info">رقم المنتج</td>
                        <td class="client-Info text-center">11115104485</td>
                        <td class="client-Info text-center">11115104485</td>
                        <td class="client-Info text-center">11115104485</td>
                        <td class="client-Info text-center">11115104485</td>
                      </tr>
                      <tr>
                        <td class="client-Info">عدد</td>
                        <td class="client-Info text-center">1</td>
                        <td class="client-Info text-center">2</td>
                        <td class="client-Info text-center">1</td>
                        <td class="client-Info text-center">1</td>
                      </tr>
                      <tr>
                        <td class="client-Info">السعر</td>
                        <td class="client-Info text-center">4214 ريال</td>
                        <td class="client-Info text-center">4214 ريال</td>
                        <td class="client-Info text-center">4214 ريال</td>
                        <td class="client-Info text-center">4214 ريال</td>
                      </tr>
                      <tr v-for="item in CustomerInfo" :key="item.name">
                        <td class="client-Info">{{ item.name }}</td>
                        <td class="client-Info text-center">
                          {{ item.calories }}
                        </td>
                        <td class="client-Info text-center">----</td>
                        <td class="client-Info text-center">----</td>
                        <td class="client-Info text-center">----</td>
                      </tr>
                    </tbody>
                  </template>
                </v-simple-table>
                <v-card dark tile flat color="green darken-1">
                  <v-card-actions class="">
                    <v-card-text class="pa-0">إجمالي السعر</v-card-text>
                    <v-card-text class="pa-0 text-center">
                      47851 ريال
                    </v-card-text>
                  </v-card-actions>
                </v-card>
              </v-card>
            </v-col>
          </v-tab-item>
        </v-tabs-items>
      </v-card>
      <v-bottom-navigation
        v-model="value"
        class="mt-50 hidden-sm-and-up"
        height="48"
        background-color="white"
        light
        hide-on-scroll
        fixed
      >
        <v-tabs
          v-model="tab"
          centered
          grow
          show-arrows=""
          background-color="white"
          slider-size="3"
          slider-color="#fc624d"
        >
          <v-tab href="#tab-1" active-class="links-active" class="links">
            الطلبات
          </v-tab>
          <v-tab href="#tab-2" active-class="links-active" class="links">
            بإنتظار شحن المنتج
          </v-tab>
          <v-tab href="#tab-4" active-class="links-active" class="links">
            الطلبات الملغية
          </v-tab>
        </v-tabs>
      </v-bottom-navigation>
    </v-container>
  </div>
</template>
<script>
export default {
  name: "UserAdd",
  components: {},
  data() {
    return {
      dialogm1: "",
      dialog: false,
      ShowTaps: false,
      text: "هل أنت متأكد من حذف الأعلان.",
      tab: null,
      CustomerInfo: [
        {
          name: " تاريخ الطلب ",
          DateTime: ["21 / 1 / 2022", "10:55 am"],
        },
        {
          name: "طلب رقم ",
          calories: "0147",
        },
        {
          name: "طلب رقم ",
          calories: "0147",
        },
      ],
      ProductInfo: [
        {
          name: "أسم المنتج",
          calories: "مـازدا مازدا3 مـازدا مازدا3 مـازدا مازدا3",
        },
        {
          name: "رقم المنتج ",
          calories: 1654218459,
        },
        {
          name: "الموديل",
          calories: 262,
        },
        {
          name: "المقاس",
          calories: 262,
        },
        {
          name: "اللون",
          calories: 262,
        },
        {
          name: "عدد",
          calories: 2,
        },
        {
          name: "إجمالي",
          calories: "1521 ريال",
        },
      ],
      ShipmentInfo: [
        {
          name: "أسم شركة التوصيل أو أسم موصل الطلب",
          calories: 159,
        },
        {
          name: "رقم هاتف التوصيل",
          calories: 237,
        },
        {
          name: "زمن توصيل المنتج",
          calories: 262,
        },
        {
          name: "رقم التوصيل ",
          calories: 159,
        },
      ],
      ShipmentArrived: [
        {
          calories: "النسر السريع",
          name: "أسم شركة التوصيل أو أسم موصل الطلب",
        },
        {
          calories: "0112151456",
          name: "رقم هاتف التوصيل",
        },
        {
          calories: 4,
          name: "زمن توصيل المنتج",
        },
        {
          name: "رقم التوصيل ",
          calories: "DE2550551",
        },
        {
          name: "عنوان التسليم",
          calories:
            "عنوانعنوانعنوانعنوانعنوانعنوانعنوانعنوان 1424 عنوانعنوانعنوانعنوانعنوان",
        },
      ],
    };
  },
  methods: {
    customFilter(item, queryText) {
      const textOne = item.name.toLowerCase();
      const textTwo = item.abbr.toLowerCase();
      const searchText = queryText.toLowerCase();

      return (
        textOne.indexOf(searchText) > -1 || textTwo.indexOf(searchText) > -1
      );
    },
    save() {
      this.hasSaved = true;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "../scss/virables";
@import "../scss/mixin";
.UserAdd {
  width: 100%;
  min-height: calc(100vh - 114px);
  @media (max-width: 600px) {
    margin-bottom: 50px;
  }
  .title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    color: #039be5 !important;
    font-size: 16px !important;
  }
  .container {
    @media (min-width: 960px) {
      max-width: 1212px !important;
    }
    @media (max-width: 450px) {
      padding: 5px !important;
    }
  }
  .btn2 {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 500 !important;
    font-size: 14px !important;
  }
  .client-Info {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 500 !important;
    font-size: 16px !important;
  }
}

::v-deep .theme--light.v-tabs .v-tab:hover:before {
  opacity: 0 !important;
}
::v-deep span.v-stepper__step__step {
  margin-left: 0;
  margin-bottom: 10px;
}
::v-deep input::placeholder {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-size: 13px;
}
.links {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-size: 15px !important;
  @media (max-width: 600px) {
    font-size: 14px !important;
    font-weight: 600;
  }
}
.links:hover {
  color: $color-2 !important;
}
.links-active {
  color: $color-2 !important;
}
::v-deep .v-item-group.v-bottom-navigation--fixed {
  z-index: 16 !important;
}
.PerPrder {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-size: 13px !important;
}
</style>
