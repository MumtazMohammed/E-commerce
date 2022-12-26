<template>
  <div>
    <!-- fillter small screen from 600px and down -->
    <div class="hidden-md-and-up filtertion">
      <v-dialog v-model="filterdialog" persistent fullscreen>
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            color="filtertion-btn"
            class="primary filtertion-btn"
            dark
            icon
            v-bind="attrs"
            v-on="on"
            elevation="0"
            width="52"
            height="52"
          >
            <v-icon>mdi-filter</v-icon>
          </v-btn>
        </template>
        <v-card class="pa-2" tile flat>
          <div>
            <v-card-text class="pa-2 text"> المناطق </v-card-text>
            <v-row no-gutters>
              <v-col class="" cols="12">
                <v-chip-group column>
                  <v-chip filter class="chip" small v-for="i in 10" :key="i">
                    تعز
                  </v-chip>
                </v-chip-group>
              </v-col>
            </v-row>
          </div>
          <v-divider class="mt-3"></v-divider>
          <div>
            <v-card-text class="pa-2 text"> ألوان </v-card-text>
            <v-row no-gutters class="justify-space-between">
              <v-col>
                <v-chip-group column>
                  <v-chip
                    v-for="PerColor in Colors"
                    :key="PerColor"
                    color=""
                    class="chip"
                    :class="PerColor.Colors"
                    small
                    filter
                    outlined
                  >
                    {{ PerColor.ColorText }}
                  </v-chip>
                </v-chip-group>
              </v-col>
            </v-row>
          </div>
          <v-divider class="mt-3"></v-divider>
          <div>
            <v-card-text class="pa-2 text"> السعر </v-card-text>
            <v-card-actions class="">
              <v-text-field
                type="number"
                dense
                hide-details=""
                outlined
                placeholder="من"
              ></v-text-field>
              <v-icon class="mx-2" color="primary">mdi-arrow-left-thin</v-icon>
              <v-text-field
                type="number"
                dense
                hide-details=""
                outlined
                placeholder="الى"
              ></v-text-field>
            </v-card-actions>
          </div>
          <v-divider class="mt-3"></v-divider>
          <div>
            <v-card-text class="pa-2 text"> الفئات </v-card-text>
            <v-row no-gutters>
              <v-col class="" cols="12">
                <v-chip-group column>
                  <v-chip filter class="chip" small v-for="i in 10" :key="i">
                    تعز
                  </v-chip>
                </v-chip-group>
              </v-col>
            </v-row>
          </div>
          <v-divider class="mt-3"></v-divider>
          <div>
            <v-card-text class="pa-2 text"> العلامة التجارية </v-card-text>
            <v-row no-gutters>
              <v-col class="" cols="12">
                <v-chip-group column>
                  <v-chip filter class="chip" small v-for="i in 10" :key="i">
                    تعز
                  </v-chip>
                </v-chip-group>
              </v-col>
            </v-row>
          </div>
          <v-divider class="mt-3"></v-divider>
          <div class="mb-4">
            <v-card-text class="pa-2 text"> الحالة </v-card-text>
            <v-row no-gutters>
              <v-col class="" cols="12">
                <v-chip-group column>
                  <v-chip filter class="chip" small v-for="i in 3" :key="i">
                    تعز
                  </v-chip>
                </v-chip-group>
              </v-col>
            </v-row>
          </div>
          <v-divider class="my-3"></v-divider>

          <v-row no-gutters>
            <v-col cols="6" class="pa-2">
              <v-btn block class="btn" @click="filterdialog = false">
                عرض
              </v-btn>
            </v-col>
            <v-col cols="6" class="pa-2">
              <v-btn block class="btn" @click="filterdialog = false">
                إلغاء
              </v-btn>
            </v-col>
          </v-row>
        </v-card>
      </v-dialog>
    </div>
    <div class="hidden-sm-and-down">
      <v-card-title class="text">
        <v-icon right color="primary" size="16">mdi-filter-outline</v-icon>
        تصفية البحث
      </v-card-title>
      <v-expansion-panels light focusable tile popout flat multiple>
        <v-expansion-panel>
          <v-expansion-panel-header color="transparent" class="text">
            المناطق
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <v-row no-gutters>
              <v-col cols="6" v-for="i in 10" :key="i">
                <v-checkbox
                  v-model="ex4"
                  label="تعز"
                  color="primary"
                  value="primary"
                  class="ma-0"
                  multiple
                  hide-details
                ></v-checkbox>
              </v-col>
            </v-row>
          </v-expansion-panel-content>
        </v-expansion-panel>
        <v-expansion-panel>
          <v-expansion-panel-header class="text">
            ألوان
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <v-row no-gutters>
              <v-col v-for="PerColor in Colors" :key="PerColor">
                <v-avatar size="15" :color="PerColor" class="ma-1"> </v-avatar>
              </v-col>
            </v-row>
          </v-expansion-panel-content>
        </v-expansion-panel>
        <v-expansion-panel>
          <v-expansion-panel-header class="text">
            الفئات
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <v-row no-gutters>
              <v-col cols="6" v-for="i in 10" :key="i">
                <v-checkbox
                  v-model="ex4"
                  label="تعز"
                  color="primary"
                  value="primary"
                  class="ma-0"
                  multiple
                  hide-details
                ></v-checkbox>
              </v-col>
            </v-row>
          </v-expansion-panel-content>
        </v-expansion-panel>
        <v-expansion-panel>
          <v-expansion-panel-header class="text">
            السعر
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <v-row no-gutters class="mt-1">
              <v-col>
                <v-text-field
                  type="number"
                  dense
                  hide-details=""
                  outlined
                  placeholder="من"
                ></v-text-field>
              </v-col>
              <v-col class="text-center">
                <v-icon color="primary"> mdi-arrow-left-thin </v-icon>
              </v-col>
              <v-col>
                <v-text-field
                  type="number"
                  dense
                  hide-details=""
                  outlined
                  placeholder="الى"
                ></v-text-field>
              </v-col>
              <v-col cols="12" class="pa-3">
                <v-btn small block elevation="0" color="primary" class="text">
                  بحث
                </v-btn>
              </v-col>
            </v-row>
          </v-expansion-panel-content>
        </v-expansion-panel>
        <v-expansion-panel>
          <v-expansion-panel-header class="text">
            العلامة التجارية
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <v-row no-gutters>
              <v-col cols="6" v-for="i in 10" :key="i">
                <v-checkbox
                  v-model="ex4"
                  label="تعز"
                  color="primary"
                  value="primary"
                  class="ma-0"
                  multiple
                  hide-details
                ></v-checkbox>
              </v-col>
            </v-row>
          </v-expansion-panel-content>
        </v-expansion-panel>
        <v-expansion-panel>
          <v-expansion-panel-header class="text">
            الحالة
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <v-row no-gutters>
              <v-col cols="6" v-for="i in 10" :key="i">
                <v-checkbox
                  v-model="ex4"
                  label="تعز"
                  color="primary"
                  value="primary"
                  class="ma-0"
                  multiple
                  hide-details
                ></v-checkbox>
              </v-col>
            </v-row>
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>
    </div>
  </div>
</template>

<script>
export default {
  name: "FilterSearch",
  components: {},
  data() {
    return {
      items: ["Foo", "Bar", "Fizz", "Buzz"],
      filterdialog: null,
      admins: [
        ["Management", "mdi-account-multiple-outline"],
        ["Settings", "mdi-cog-outline"],
      ],
      cruds: [
        ["Create", "mdi-plus-outline"],
        ["Read", "mdi-file-outline"],
        ["Update", "mdi-update"],
        ["Delete", "mdi-delete"],
      ],
      Colors: [
        { ColorText: "أحمر", Colors: "red" },
        { ColorText: "برتقالي", Colors: "orange" },
        { ColorText: "أصفر", Colors: "yellow" },
        { ColorText: "أخضر", Colors: "green" },
        { ColorText: "أزرق", Colors: "blue" },
        { ColorText: "بنفسجي", Colors: "purple" },
        { ColorText: "زهري", Colors: "pink" },
        { ColorText: "بنى", Colors: "brown" },
        { ColorText: "رمادي", Colors: "grey" },
        { ColorText: "أسود", Colors: "black" },
        { ColorText: "أبيض", Colors: "white" },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";

.filtertion {
  position: fixed;
  z-index: 6;
  left: 8px;
  bottom: 46px;
}
.filtertion-btn {
  letter-spacing: 0 !important;
  font-size: 18px;
  font-family: $fontfamliy3;
  transform: scale(0.8);
}
.btn {
  letter-spacing: 0 !important;
  font-size: 18px;
  font-family: $fontfamliy3;
  color: $fontcolorlinks !important;
  @media (max-width: 600px) {
    font-size: 15px !important;
  }
}
// ::v-deep .v-dialog.v-dialog--active.v-dialog--persistent {
//   margin: 5px;
// }

::v-deep input {
  font-family: $fontfamliy3;
  font-size: 14px !important;
  letter-spacing: 0;
}

.text {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-size: 14px !important;
  color: $color-2;
  font-weight: 600;
}
.ac {
  background-color: $color-2;
  color: #fff !important;
}
.chip {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  font-size: 14px !important;
}
::v-deep .theme--light.v-chip--active:before {
  opacity: 0 !important;
}
// ::v-deep .v-input--selection-controls__input {
//   margin-right: 3px;
//   @media (max-width: 600px) {
//     margin-right: 7px;
//   }
// }
// ::v-deep .v-chip.v-size--default {
//   height: 30px;
//   border-radius: 2px !important;
// }
/* Chrome, Safari, Edge, Opera */
::v-deep input::-webkit-outer-spin-button,
::v-deep input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
/* Firefox */
::v-deep .v-input__slot {
  min-height: 25px !important;
  justify-content: center;
}
::v-deep .v-avatar {
  @media (max-width: 600px) {
    height: 22px !important;
    min-width: 22px !important;
    width: 22px !important;
  }
}
::v-deep .v-expansion-panel-content__wrap {
  padding: 0px 10px 10px;
}
::v-deep label.v-label.theme--light {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
}
</style>
