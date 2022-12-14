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
            <v-checkbox
              v-for="i in 10"
              :key="i"
              v-model="ex4"
              label="تعز"
              color="primary"
              value="primary"
              class="ma-0"
              multiple
              hide-details
            ></v-checkbox>
          </div>
          <v-divider class="mt-3"></v-divider>
          <div>
            <v-card-text class="pa-2 text"> ألوان </v-card-text>
            <v-card-actions
              class="grey lighten-2 justify-center"
              style="flex-wrap: wrap"
            >
              <v-avatar
                v-for="PerColor in Colors"
                :key="PerColor"
                size="15"
                :color="PerColor"
                class="ma-1"
              >
              </v-avatar>
            </v-card-actions>
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
            <v-checkbox
              v-model="ex4"
              label="تعز"
              color="primary"
              value="primary"
              class="ma-0"
              hide-details
            ></v-checkbox>
          </div>
          <v-divider class="mt-3"></v-divider>
          <div>
            <v-card-text class="pa-2 text"> العلامة التجارية </v-card-text>
            <v-checkbox
              v-model="ex4"
              label="تعز"
              color="primary"
              value="primary"
              class="ma-0"
              hide-details
            ></v-checkbox>
          </div>
          <v-divider class="mt-3"></v-divider>
          <div class="mb-4">
            <v-card-text class="pa-2 text"> الحالة </v-card-text>
            <v-checkbox
              v-model="ex4"
              label="تعز"
              color="primary"
              value="primary"
              class="ma-0"
              hide-details
            ></v-checkbox>
          </div>
          <v-divider class="my-3"></v-divider>

          <v-card-actions class="">
            <v-btn
              rounded
              elevation="0"
              color="green "
              class="btn"
              @click="filterdialog = false"
            >
              عرض
            </v-btn>
            <v-spacer></v-spacer>
            <v-btn
              rounded
              elevation="0"
              color="red darken-1 "
              class="btn"
              @click="filterdialog = false"
            >
              إلغاء
            </v-btn>
          </v-card-actions>
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
        "red",
        "orange",
        "yellow",
        "green",
        "blue",
        "purple",
        "pink",
        "brown",
        "grey",
        "black",
        "white",
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
  color: #fff !important;
  font-weight: 600;
}
// ::v-deep .v-dialog.v-dialog--active.v-dialog--persistent {
//   margin: 5px;
// }
::v-deep .v-select__selection.v-select__selection--comma {
  font-family: $fontfamliy3;
  font-size: 14px;
  letter-spacing: 0;
}
::v-deep .v-list-item__title {
  font-family: $fontfamliy3;
  font-size: 14px !important;
  letter-spacing: 0;
}
::v-deep input {
  font-family: $fontfamliy3;
  font-size: 14px !important;
  letter-spacing: 0;
}
::v-deep .v-list-group__header.v-list-item.v-list-item--link.theme--light {
  color: $fontcolorlinks;
  font-family: $fontfamliy3;
}
::v-deep .v-list--dense .v-list-item .v-list-item__title {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-size: 14px !important;
}
::v-deep i.v-icon.notranslate.material-icons.theme--light {
  font-size: 16px !important;
}
.text {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-size: 14px !important;
  color: $fontcolorlinks;
}
::v-deep .v-input--selection-controls__ripple {
  border-radius: 50%;
  cursor: pointer;
  height: 25px;
  position: absolute;
  transition: inherit;
  width: 24px;
  left: 0px;
  top: calc(0% - 0px);
  margin: 0px !important;
}
::v-deep .v-input--selection-controls__input {
  margin-right: 3px;
  @media (max-width: 600px) {
    margin-right: 7px;
  }
}
::v-deep .v-chip.v-size--default {
  height: 30px;
  border-radius: 2px !important;
}
/* Chrome, Safari, Edge, Opera */
::v-deep input::-webkit-outer-spin-button,
::v-deep input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
/* Firefox */
::v-deep .v-input__slot {
  min-height: 25px !important;
}
::v-deep .v-input__slot input {
  text-align: center;
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-size: 11px !important;
  @media (max-width: 600px) {
    font-size: 15px !important;
  }
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
</style>
